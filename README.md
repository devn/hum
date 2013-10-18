# hum

A ClojureScript attempt at wrapping some of the HTML5 Web Audio API functions to create audio, synthesizers, mostly noise, and maybe someday music.

## Usage
Add this to your requires in `project.clj`:

```clojure
  [hum "0.2.2"]
```

Here's an example:
```clojure
(ns myapp.core
  (:require [hum.core :as hum])

(def ctx (hum/create-context))
(def vco (hum/create-osc ctx :sawtooth))
(def vcf (hum/create-biquad-filter ctx))
(def output (hum/create-gain ctx))

(hum/connect vco vcf)
(hum/connect vcf output)

(hum/start-osc ctx vco)

(hum/connect output (.-destination ctx))

(hum/note-on ctx output vco 440)
```

## What now? / Contributing

If you are using `hum` in your app, I'd love to hear about it. If you want to suggest functionality, then please submit an Issue, or even better, a Pull Request! I'd like to build up an API of functions that people find useful for making music and software instruments, but I'll need your help to get there. Thanks in advance!

## License

Copyright © 2013 Matt Gauger.

Distributed under the Eclipse Public License version 1.0 or (at
your option) any later version.
