observable.pipe to apply one or more operators to manipulate the source stream
shareReplay to share subscription with observers
concat to concatenate observables in sequence. Eg: concat initial results with filtered results 
fromPromise to create an observable from a promise
concatMap to map one observable with another only when later is done emitting. Eg: pre save on form.valueChange only when save has completed
merge to process multiple observables at once. Eg: multiple http calls in parellel
mergeMap to map one observable with another another for emitting multiple times. Eg: pre save on every form.valueChange
fromEvent to create an observable from events
exhaustMap to map source observable with another observable and ignore values from source observable while output observable is still running. Eg: ignoring multiple save button clicks while response of save has not arrived
fetch api is cancellable using new AbortController().abort()
debounceTime to take tail values stable for given time
distinctUntilChanged to filter duplicate
switchMatch to unsubscribe from ongoing output on new source observable values. Eg: search typeahead to cancel previous api request on new search text
catchError to catch error n provide alternate recovery observable in response or rethrow the error, or retry again
of to create an observable from an array of values
throwError to create an observable that immediately errors out with given error
finalize to cleanup after observable completes or errors out
catchError before other pipeable functions to bypass the chaining of subsequent observables
finalize before shareReplay to avoid its multiple invocation
retryWhen(errors => errors.pipe(delayWhen(() => timer(2000)))) to retry after 2s on every error
startWith to initialize a stream with initial value
debounceTime to emit stable tail/latest values for given time. Eg: search text
throttle to emit source observable values on completion of auxiliary observable.  Eg: stream of stock price
throttleTime to limit number of emitted values for given time by taking initial value.
Custom operator: const opFn = (...args) => (source: Observable<any>) => source.pipe(tap(val => { // Use args here }))
forkJoin to observable multiple streams and join their values as tuples
Usecases of subject
Source not observable
Multicast
Private data
No unsubscribe
No persistent state
Const observable = new Subject().asObservable()
BehaviorSubject(initialValue)
Persistent initial or last state
Always provides a value
AsyncSubject for long running observables to get only the last value after completion. Emits last value for late subscribers
ReplaySubject to replay all emitted values to late subscribers
Store using BehaviorSubject
Component is pure projection of state
first() to complete the observable on first emitted value
take(n) to complete the observable on nth emitted value
withLatestFrom to combine value of source observable with latest values from other observables. Eg: combine lessons with latest courses
share() === publish(), refCount()
publish() === multicast(new Subject())
Nn
