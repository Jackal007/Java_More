> WeakHashMap，此种Map的特点是，当除了自身有对key的引用外，此key没有其他引用那么此map会自动丢弃此值，
>
> 见实例：
>
> 此例子中声明了两个Map对象，一个是HashMap，一个是WeakHashMap，同时向两个map中放入a、b两个对象（只有一份，两个map存的都是对它的引用），当HashMap  remove掉a 并且将a、b都指向null时，WeakHashMap中的a将自动被回收掉。出现这个状况的原因是，对于a对象而言，当HashMap  remove掉并且将a指向null后，除了WeakHashMap中还保存a外已经没有指向a的指针了，所以WeakHashMap会自动舍弃掉a，而对于b对象虽然指向了null，但HashMap中还有指向b的指针，所以WeakHashMap将会保留



