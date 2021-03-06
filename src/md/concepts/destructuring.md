# Destructuring in Clojure

In Clojure, destructuring is a shorthand for assigning names to parts
of data structures based on their forms. Don't worry if that's
confusing at first, it becomes very clear with a few examples.

Suppose we have a function that prints a greeting based on a user's
name, title, and location.

Here we'll manually pull out the name, title, and location from the
`user` parameter (a Map), and create bindings named `name`, `title`,
and `location` via [`let`](/clojure.core/let).

```
(defn greet [user]
  (let [name (:name user)
        location (:location user)]
    (println "Hey there" name ", how's the weather in" location "?")))

(greet {:name "Josie" :location "San Francisco"})
;; Hey there Josie, how's the weather in San Francisco?
;;=> nil

(greet {:name "Ivan" :location "Moscow"})
;; Hey there Ivan, how's the weather in Moscow?
;;=> nil

```

Destructuring lets us specify naming of the parameters directly from the
structure of the passed map:

```
(defn greet2 [{:keys [name location]}]
  (println "Hey there" name ", how's the weather in" location "?"))

(greet2 {:name "Josie" :location "San Francisco"})
;; Hey there Josie, how's the weather in San Francisco?
;;=> nil


```

See John Del Rosario's [destructuring cheat sheet](http://john2x.com/blog/clojure-destructuring/) for a more comprehensive overview.
