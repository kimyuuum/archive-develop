# Java Reference

Strong > Soft > Weak > Unreachable  ——> 순으로 GC 수거 확률이 증가한다.

### Soft Reference

JVM의 GC가 메모리가 부족하다고 판단하면 수거한다. 수거를 아예 막지는 못하지만, 지연은 가능하다. 자주 사용될수록 GC가 수거하지 않는다.

### Weak Reference

가장 흔한 reference. 명시적으로 weak reference를 사용하여 해당 객체가 GC되도록 유도 가능하다. GC가 돌면 수거하는 객체이다.