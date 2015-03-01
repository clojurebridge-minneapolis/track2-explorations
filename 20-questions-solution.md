
To represent a node as a closure instead of a data structure:

```Clojure
(defn make-node [contents yes no]
  (if yes
    (fn [network]
      (println contents)
      (when-let [f (network (if (= "y" (read-line)) yes no))]
        (f network)))
    (fn [network]
      contents)))
```

To compile a static data structure:

```Clojure
(defn compile-net [network node-name]
  (when-let [{:keys [contents yes no]} (network node-name)]
    (if yes
      (let [yes-fn (compile-net network yes)
            no-fn (compile-net network no)]
        (fn []
          (println contents)
          (if (= "y" (read-line))
            (yes-fn)
            (no-fn))))
      (fn []
        contents))))
```