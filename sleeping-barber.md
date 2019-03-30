# sleeping-barber-problem-solution-using-semaphore


```c
semaphore customers = 0;

semaphore barbers=0;

semaphore mutex=1;

int waiting=0;


void barber(void)

{

 while (TRUE) {

  P(customers);          /*go to sleep if no customers*/

  P(mutex);

  waiting=waiting-1;

  V(barbers);

  V(mutex);

  cut_hair();

 }

}



void customer(void)

{

 P(mutex);

 if (waiting lessthan CHAIRS) {

  waiting=waiting+1;

  V(customers);

  V(mutex);

  P(barbers);

  get_haircut();

 } else {

    V(mutex);

 }

}
```

