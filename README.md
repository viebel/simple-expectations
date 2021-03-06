# simple-expectations

Using test.check with expectations is simple, but the standard failure message leaves a bit to
be desired in my opinon. However, you can use an expectations.CustomPred and get much better
failure reports when things go poorly.

## The Example Tests

[jump to tests](https://github.com/jaycfields/simple-expectations/blob/master/test/simple_expectations/core_test.clj)

## Output

```clojure
;;; results from using expectations and simple-check without a CustomPred
failure in (core_test.clj:18) : simple-expectations.core-test
(expect {:result true} (in (sc/quick-check 100 prop-no-42)))

           expected: {:result true}
                 in: {:result false, :failing-size 42, :num-tests 43, :fail [[7 -16 0 33 -37 42 -36]], :shrunk {:total-nodes-visited 14, :depth 6, :result false, :smallest [[42]]}}

           :result expected: true
                        was: false

;;; results from using expectations and simple-check with a CustomPred
failure in (core_test.clj:31) : simple-expectations.core-test
(expect (->SimpleCheck) (sc/quick-check 100 prop-no-42))

           52 of 53 failures
           fail: [[-8 -29 -37 -37 -15 36 -22 9 52 -6 -15 1 5 16 -6 5 -17 -10 -48 16 29 20 -21 42 45 -45 -42 37 36 31 28 -33 -24 -7 1]]
           shrunk: [[42]]

Ran 2 tests containing 2 assertions in 84 msecs
2 failures, 0 errors.
```

## License

Copyright © 2014 FIXME

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
