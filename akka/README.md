[akka第三方资源](http://ifeve.com/category/framework/akka/)
[akka官方资源]（https://doc.akka.io/docs/akka/current/）

```
    private LinkedList<String> getChildren(String path) {
        LinkedList<String> strings = new LinkedList<>();
        system.actorSelection(path).resolveOne(new Timeout(new FiniteDuration(1, TimeUnit.MINUTES)))
                .onComplete((Function1<Try<ActorRef>, Object>) v1 -> {
                    //普通actor转换成RepointableActorRef
                    RepointableActorRef repointableActorRef = (RepointableActorRef) v1.get();
                    strings.add(repointableActorRef.path().name());
                    repointableActorRef.children().foreach(new Function1<ActorRef, LinkedList<String>>() {
                        @Override
                        public LinkedList<String> apply(ActorRef v1) {
                           return getChildren(v1.path().name());
                        }
                    });

                    return strings;
                }, executionContext);
        return strings;
    }

    @Test
    //遍历所有的ACTOR
    public void whenRequest_thenActorResponds() {
        LinkedList<String> strings = new LinkedList<>();
        system.actorSelection("/user/").resolveOne(new Timeout(new FiniteDuration(1, TimeUnit.MINUTES)))
                .onComplete((Function1<Try<ActorRef>, Object>) v1 -> {
                    // /user: 守护角色与这个角色打交道最多的就是用户创建角色的父角色。我们将其命名为“/user”。所有以system.actorOf()创建的角色都是它的子角色。这意味着当这个角色终止时，
                    //系统中所有的普通角色也都将被关闭。同时，这也意味着这个守护者的监管策略决定了最顶层的普通角色是怎样被监管的。从Akka版本2.1以后，可以通过配置akka.actor.guardian-supervisor-strategy
                   // 来设置它。它的值必须是一个SupervisorStrategyConfigurator类的全路径。当该守护者向上汇报失败时，根守护者的响应就是终止该守护者，即停止整个角色系统。

                    LocalActorRef localActorRef = (LocalActorRef) v1.get();
                    strings.add(localActorRef.path().name());
                    localActorRef.children().foreach(new Function1<ActorRef, Object>() {
                        @Override
                        public Object apply(ActorRef v1) {
                            getChildren(v1.path().name());
                            return null;
                        }
                    });

                    return localActorRef;
                }, executionContext);
    }
```