# producer-consumer-solution-using-semaphore

```c
BufferSize = 3;

semaphore mutex = 1;              // Controls access to critical section

semaphore empty = BufferSize;     // counts number of empty buffer slots

semaphore full = 0;               // counts number of full buffer slots

Producer()
{
  int widget;

  while (TRUE) {                  // loop forever
    make_new(widget);             // create a new widget to put in the buffer
    down(&empty);                 // decrement the empty semaphore
    down(&mutex);                 // enter critical section
    put_item(widget);             // put widget in buffer
    up(&mutex);                   // leave critical section
    up(&full);                    // increment the full semaphore
    }
}

Consumer()
{
  int widget;
    
  while (TRUE) {                  // loop forever
    down(&full);                  // decrement the full semaphore
    down(&mutex);                 // enter critical section
    remove_item(widget);          // take a widget from the buffer
    up(&mutex);                   // leave critical section
    up(&empty);                   // increment the empty semaphore
    consume_item(widget);         // consume the item
    }
}
```

