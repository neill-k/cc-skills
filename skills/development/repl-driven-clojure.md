---
name: repl-driven-clojure
description: Master REPL-driven development workflow for Clojure 1.12 with live coding, rich comment blocks, state management, and iterative design
---

# REPL-Driven Development with Clojure

When the user requests guidance on Clojure development, REPL workflow, interactive programming, or asks how to structure Clojure code for rapid iteration, use this skill to provide comprehensive REPL-driven development guidance using Clojure 1.12 conventions.

## Core Principles

1. **Live Interaction**: Code with immediate feedback through continuous evaluation
2. **Bottom-Up Development**: Build and test small functions, composing into larger systems
3. **Incremental Growth**: Make small changes, evaluate constantly, refine iteratively
4. **State Awareness**: Manage application state explicitly for reliable REPL sessions
5. **Documentation in Code**: Use rich comment blocks as living documentation
6. **Fast Feedback Loop**: Seconds from idea to working code

## When to Use This Skill

Activate this skill when the user:
- Requests help with Clojure development workflow
- Asks about REPL-driven development or interactive programming
- Wants to structure Clojure code for iterability
- Needs guidance on namespace management and reloading
- Asks about state management in long-running REPL sessions
- Wants to combine REPL-driven and test-driven development
- Mentions "rich comment blocks" or "design journals"
- Asks about Clojure 1.12 features or conventions

## REPL-Driven Development Framework

### The REPL Cycle

**Read → Evaluate → Print → Loop**

1. **Read**: Clojure reader processes code and expands macros
2. **Evaluate**: Code compiles to JVM bytecode and executes
3. **Print**: Results display in REPL or application
4. **Loop**: Continue with next expression

### Development Workflow

**Standard Flow:**
1. Start REPL connected to your editor
2. Write function in source file
3. Evaluate expression in namespace context
4. Inspect results, refine implementation
5. Iterate until satisfied
6. Write tests to codify successful experiments
7. Repeat for next function

## Clojure 1.12 Features and Conventions

### Qualified Methods (New in 1.12)

Clojure 1.12 simplifies Java interop with uniform `Classname/member` syntax:

```clojure
;; Instance methods - NEW uniform syntax
(String/length "hello")  ; => 5
(String/toUpperCase "hello")  ; => "HELLO"

;; Constructors with Classname/new
(java.util.ArrayList/new)  ; Create ArrayList
(String/new "hello")  ; Create String

;; Works with type hints for performance
(defn process-string [^String s]
  (String/length s))
```

### Method Values (New in 1.12)

Reference methods as values using qualified method syntax:

```clojure
;; Method values
(map String/length ["foo" "hello" "world"])
;; => (3 5 5)

;; Pass as higher-order functions
(filter (String/startsWith "hel") ["hello" "world" "help"])
;; => ("hello" "help")
```

### Param Tags (Renamed in 1.12)

Type hints for method parameters (formerly `:arg-tags`):

```clojure
;; Use :param-tags for explicit method selection
(defn add-numbers
  {:param-tags [Long Long]}
  [^long a ^long b]
  (+ a b))
```

### Array Class Syntax (Updated in 1.12)

New streamlined array class syntax:

```clojure
;; OLD: String-*
;; NEW: String*
(defn process-array [^String* arr]
  (alength arr))

;; Multi-dimensional arrays
(defn matrix [^int** grid]
  (aget grid 0 0))
```

## Rich Comment Blocks

Rich comment blocks are living documentation that capture interactive exploration:

```clojure
(ns myapp.core
  (:require [clojure.string :as str]))

(defn greet [name]
  (str "Hello, " name "!"))

(comment
  ;; REPL experiments and usage examples
  ;; Evaluate these expressions with your editor

  ;; Basic usage
  (greet "Alice")
  ;; => "Hello, Alice!"

  ;; Edge cases
  (greet "")
  ;; => "Hello, !"

  (greet nil)
  ;; => NullPointerException - need to handle!

  ;; Fixed version exploration
  (defn greet-safe [name]
    (str "Hello, " (or name "stranger") "!"))

  (greet-safe nil)
  ;; => "Hello, stranger!"

  ;; Test with various inputs
  (map greet-safe ["Alice" "Bob" nil ""])
  ;; => ("Hello, Alice!" "Hello, Bob!" "Hello, stranger!" "Hello, stranger!")

  :rcf) ;; Rich Comment Form marker
```

### Best Practices for Comment Blocks

**Structure:**
```clojure
(comment
  ;; Section: System Startup
  (start-system!)
  (reset-system!)

  ;; Section: Data Exploration
  (def sample-data {...})
  (process sample-data)

  ;; Section: Performance Testing
  (time (expensive-operation))

  ;; Section: Debugging Helpers
  (println "Debug:" (capture-state))

  :rcf)
```

## Design Journals

Create separate namespaces to document design decisions:

```clojure
(ns myapp.design-journal
  "Living record of design decisions and explorations"
  (:require [myapp.core :as core]))

(comment
  ;; Decision: Data structure for user sessions
  ;; Date: 2025-01-10
  ;; Context: Need to track active user sessions with timeout

  ;; Option 1: Simple map (REJECTED)
  ;; - Pro: Easy to understand
  ;; - Con: No automatic cleanup, memory leak risk
  (def sessions-v1
    {:user-123 {:started-at (System/currentTimeMillis)}})

  ;; Option 2: core.cache with TTL (CHOSEN)
  ;; - Pro: Automatic expiration
  ;; - Pro: Battle-tested library
  ;; - Con: Additional dependency
  (require '[clojure.core.cache :as cache])
  (def sessions-v2
    (cache/ttl-cache-factory {} :ttl 3600000))

  ;; Rationale: Automatic cleanup is critical for production
  ;; Alternative considered: Redis (overkill for this use case)

  :rcf)
```

## State Management for Long-Running REPLs

### Using Mount

```clojure
(ns myapp.core
  (:require [mount.core :as mount :refer [defstate]]))

;; Define stateful components
(defstate database
  :start (connect-db!)
  :stop (disconnect-db database))

(defstate http-server
  :start (start-server! {:port 3000})
  :stop (stop-server! http-server))

(comment
  ;; REPL workflow with Mount

  ;; Start all states
  (mount/start)

  ;; Restart specific state after code changes
  (mount/stop #'database)
  (mount/start #'database)

  ;; Restart entire system
  (mount/stop)
  (mount/start)

  :rcf)
```

### Using Integrant

```clojure
(ns myapp.system
  (:require [integrant.core :as ig]))

;; Define system configuration
(def config
  {:adapter/database {:uri "jdbc:postgresql://localhost/mydb"}
   :handler/api {:db (ig/ref :adapter/database)}
   :server/http {:port 3000
                 :handler (ig/ref :handler/api)}})

;; Define component lifecycle
(defmethod ig/init-key :adapter/database [_ {:keys [uri]}]
  (connect-db uri))

(defmethod ig/halt-key! :adapter/database [_ db]
  (disconnect-db db))

(comment
  ;; REPL workflow with Integrant

  ;; Initialize system
  (def system (ig/init config))

  ;; Access components
  (:adapter/database system)

  ;; Reload with changes
  (def system (ig/suspend! system))
  (def system (ig/resume config system))

  ;; Complete restart
  (ig/halt! system)
  (def system (ig/init config))

  :rcf)
```

### Using Component

```clojure
(ns myapp.system
  (:require [com.stuartsierra.component :as component]))

(defrecord Database [uri connection]
  component/Lifecycle
  (start [this]
    (println "Starting database")
    (assoc this :connection (connect-db uri)))
  (stop [this]
    (println "Stopping database")
    (disconnect-db connection)
    (assoc this :connection nil)))

(defn new-database [uri]
  (map->Database {:uri uri}))

(comment
  ;; REPL workflow with Component

  (def db (new-database "jdbc:postgresql://localhost/mydb"))
  (def db (component/start db))

  ;; Use the component
  (:connection db)

  ;; Stop when done
  (def db (component/stop db))

  :rcf)
```

## Namespace Management

### Reloading Namespaces

```clojure
(ns user
  (:require [clojure.tools.namespace.repl :refer [refresh refresh-all]]))

(comment
  ;; Reload changed namespaces
  (refresh)

  ;; Reload all namespaces (full reset)
  (refresh-all)

  ;; Clear namespace before reload
  (require '[myapp.core :as core] :reload)

  ;; Force reload dependencies
  (require '[myapp.core :as core] :reload-all)

  :rcf)
```

### User Namespace Setup

Create `dev/user.clj` for REPL utilities:

```clojure
(ns user
  "REPL utilities and system management"
  (:require [clojure.tools.namespace.repl :as repl]
            [mount.core :as mount]
            [myapp.core :as core]))

(defn start
  "Start the system"
  []
  (mount/start))

(defn stop
  "Stop the system"
  []
  (mount/stop))

(defn reset
  "Stop, reload code, restart"
  []
  (stop)
  (repl/refresh :after 'user/start))

(comment
  ;; Quick system operations in REPL
  (start)
  (stop)
  (reset)

  :rcf)
```

## Combining REPL-Driven and Test-Driven Development

### Workflow Integration

```clojure
(ns myapp.core-test
  (:require [clojure.test :refer [deftest is testing]]
            [myapp.core :as core]))

;; Start with REPL exploration
(comment
  ;; Experiment with function behavior
  (core/parse-email "user@example.com")
  ;; => {:local "user" :domain "example.com"}

  (core/parse-email "invalid")
  ;; => nil (or should it throw?)

  ;; Try different approaches
  (defn parse-email-v2 [s]
    (when-let [[_ local domain] (re-matches #"(.+)@(.+)" s)]
      {:local local :domain domain}))

  (parse-email-v2 "user@example.com")
  ;; => {:local "user" :domain "example.com"}

  (parse-email-v2 "invalid")
  ;; => nil (good!)

  :rcf)

;; Codify successful experiments as tests
(deftest parse-email-test
  (testing "valid email"
    (is (= {:local "user" :domain "example.com"}
           (core/parse-email "user@example.com"))))

  (testing "invalid email"
    (is (nil? (core/parse-email "invalid"))))

  (testing "edge cases"
    (is (nil? (core/parse-email "")))
    (is (nil? (core/parse-email nil)))))
```

### Rich Comment Form (RCF) Testing

Use RCF-style tests for rapid feedback:

```clojure
(ns myapp.core
  (:require [hyperfiddle.rcf :refer [tests]]))

(defn add [a b]
  (+ a b))

(tests
  "basic addition"
  (add 2 3) := 5
  (add 0 0) := 0
  (add -1 1) := 0

  "works with different number types"
  (add 1.5 2.5) := 4.0
  (add 1/2 1/2) := 1)

;; Tests run automatically when namespace loads in REPL
;; Fast feedback without leaving your code
```

## Data Inspection and Visualization

### Portal Integration

```clojure
(ns user
  (:require [portal.api :as portal]))

(def p (portal/open))

(comment
  ;; Send data to Portal for inspection
  (portal/submit {:users [{:name "Alice" :age 30}
                          {:name "Bob" :age 25}]})

  ;; Tap values automatically
  (add-tap portal/submit)
  (tap> {:event "user-login" :user-id 123})

  ;; Clear portal
  (portal/clear)

  ;; Close portal
  (portal/close)

  :rcf)
```

### CIDER Inspector

```clojure
(comment
  ;; Inspect complex data structures
  (require '[cider.inspector :as inspect])

  (def complex-data
    {:users [{:id 1 :name "Alice" :orders [...]}
             {:id 2 :name "Bob" :orders [...]}]
     :metadata {...}})

  ;; Evaluate with inspector (in CIDER/Emacs)
  ;; C-c M-i to inspect result
  complex-data

  :rcf)
```

## Performance and Profiling in REPL

### Basic Timing

```clojure
(comment
  ;; Quick timing
  (time (expensive-operation))
  ;; "Elapsed time: 1234.56 msecs"

  ;; Multiple runs for average
  (dotimes [_ 5]
    (time (expensive-operation)))

  :rcf)
```

### Criterium for Accurate Benchmarking

```clojure
(ns myapp.perf
  (:require [criterium.core :as crit]))

(comment
  ;; Accurate benchmarking with JVM warmup
  (crit/quick-bench
    (reduce + (range 1000)))

  ;; Detailed benchmark
  (crit/bench
    (my-function args))

  ;; Compare implementations
  (crit/quick-bench (map inc (range 1000)))      ; lazy
  (crit/quick-bench (mapv inc (range 1000)))     ; eager
  (crit/quick-bench (into [] (map inc) (range 1000))) ; transducer

  :rcf)
```

## Debugging Techniques

### Tap and Inspect

```clojure
(defn complex-function [data]
  (let [step1 (process-step-1 data)
        _ (tap> {:stage :step1 :result step1})  ; Debug point
        step2 (process-step-2 step1)
        _ (tap> {:stage :step2 :result step2})  ; Debug point
        step3 (process-step-3 step2)]
    step3))

(comment
  ;; Set up tap handler
  (add-tap println)
  ;; or
  (add-tap portal/submit)

  ;; Run function and inspect tapped values
  (complex-function test-data)

  ;; Remove tap when done
  (remove-tap println)

  :rcf)
```

### Scope Capture

```clojure
(ns myapp.debug
  (:require [sc.api :as sc]))

(defn buggy-function [x y]
  (let [a (+ x y)
        b (* a 2)
        c (sc/spy (/ b (- y x)))]  ; Capture scope here
    (+ a b c)))

(comment
  ;; When exception occurs, inspect captured scope
  (buggy-function 5 5)  ; Division by zero!

  ;; View last exception with scope
  (sc/defsc 1)  ; Define scope from last capture

  ;; Inspect variables
  ep-1-a  ; => 10
  ep-1-b  ; => 20
  ep-1-x  ; => 5
  ep-1-y  ; => 5

  :rcf)
```

## REPL-Driven Development Patterns

### Exploratory Development Pattern

```clojure
(comment
  ;; 1. Start with data
  (def sample-users
    [{:id 1 :name "Alice" :email "alice@example.com"}
     {:id 2 :name "Bob" :email "bob@example.com"}])

  ;; 2. Explore transformations
  (map :name sample-users)
  ;; => ("Alice" "Bob")

  (group-by :id sample-users)
  ;; => {1 [{:id 1 ...}], 2 [{:id 2 ...}]}

  ;; 3. Build helper functions
  (defn by-id [users]
    (reduce (fn [acc user]
              (assoc acc (:id user) user))
            {}
            users))

  (by-id sample-users)
  ;; => {1 {:id 1 ...}, 2 {:id 2 ...}}

  ;; 4. Refine based on REPL feedback
  (defn index-by [key-fn coll]
    (into {} (map (juxt key-fn identity)) coll))

  (index-by :id sample-users)
  ;; => {1 {:id 1 ...}, 2 {:id 2 ...}}

  ;; 5. Extract to source file
  ;; 6. Write tests
  ;; 7. Move on to next function

  :rcf)
```

### Bottom-Up Composition Pattern

```clojure
;; Start with smallest pieces
(defn parse-int [s]
  (Integer/parseInt s))

(comment
  (parse-int "42")  ; => 42
  (parse-int "abc") ; => NumberFormatException
  :rcf)

;; Add error handling
(defn parse-int-safe [s]
  (try
    (Integer/parseInt s)
    (catch NumberFormatException _
      nil)))

(comment
  (parse-int-safe "42")  ; => 42
  (parse-int-safe "abc") ; => nil
  :rcf)

;; Compose into larger function
(defn sum-string-numbers [strings]
  (->> strings
       (keep parse-int-safe)
       (reduce +)))

(comment
  (sum-string-numbers ["1" "2" "3"])    ; => 6
  (sum-string-numbers ["1" "abc" "3"]) ; => 4
  :rcf)
```

### Refactoring with REPL Safety Net

```clojure
(comment
  ;; Original implementation
  (defn process-order-v1 [order]
    (let [total (reduce + (map :price (:items order)))
          discount (if (:premium? (:user order))
                     (* total 0.1)
                     0)
          final (- total discount)]
      {:order-id (:id order)
       :total final}))

  ;; Test current behavior before refactoring
  (def test-order
    {:id 123
     :user {:premium? true}
     :items [{:price 100} {:price 50}]})

  (process-order-v1 test-order)
  ;; => {:order-id 123, :total 135.0}

  ;; Refactor: extract functions
  (defn calculate-total [items]
    (reduce + (map :price items)))

  (defn calculate-discount [total premium?]
    (if premium? (* total 0.1) 0))

  (defn process-order-v2 [order]
    (let [total (calculate-total (:items order))
          discount (calculate-discount total (get-in order [:user :premium?]))
          final (- total discount)]
      {:order-id (:id order)
       :total final}))

  ;; Verify behavior unchanged
  (= (process-order-v1 test-order)
     (process-order-v2 test-order))
  ;; => true ✓

  ;; Safe to replace!

  :rcf)
```

## Editor Integration Best Practices

### Key Bindings (CIDER/Emacs)

- `C-c C-k` - Load/evaluate current buffer
- `C-c C-c` - Evaluate defn at point
- `C-M-x` - Evaluate top-level form
- `C-c M-n M-n` - Switch REPL namespace to current file
- `C-c C-v C-f` - Show function definition
- `C-c C-d C-d` - Show documentation

### Key Bindings (Calva/VS Code)

- `Ctrl+Alt+C Enter` - Load current file
- `Ctrl+Enter` - Evaluate current form
- `Alt+Enter` - Evaluate form and replace with result
- `Ctrl+Alt+C Space` - Evaluate selected text
- `Ctrl+Alt+C C` - Evaluate to comment

### Key Bindings (Cursive/IntelliJ)

- `Ctrl+Shift+L` - Load file in REPL
- `Ctrl+Shift+P` - Send form to REPL
- `Alt+Shift+P` - Send top-level form to REPL
- `Ctrl+Shift+M` - Run tests in namespace

## Common Pitfalls and Solutions

### Pitfall 1: Stale Namespace State

**Problem**: Old definitions linger after code changes

```clojure
(comment
  ;; Define function
  (defn old-function [x] (* x 2))

  ;; Later, rename to new-function in source
  ;; But old-function still exists in REPL!

  (old-function 5) ; => Still works! Bug risk!

  ;; Solution: Reload namespace
  (require '[myapp.core :as core] :reload)
  ;; or use refresh
  (require '[clojure.tools.namespace.repl :refer [refresh]])
  (refresh)

  :rcf)
```

### Pitfall 2: Circular Dependencies

**Problem**: Namespace reload fails due to circular deps

**Solution**: Restructure namespaces or use protocols

```clojure
;; Bad: Circular dependency
;; user.clj requires admin.clj
;; admin.clj requires user.clj

;; Good: Extract shared protocol
;; protocol.clj - defines interfaces
;; user.clj - requires protocol.clj
;; admin.clj - requires protocol.clj
```

### Pitfall 3: Side Effects in Top-Level

**Problem**: Code executes on namespace load

```clojure
;; Bad: Runs every load
(def db-connection (connect-to-db!))

;; Good: Defer until explicitly called
(defn get-db-connection []
  (or @db-conn-atom (reset! db-conn-atom (connect-to-db!))))

;; Or use mount/integrant/component
(defstate db-connection
  :start (connect-to-db!)
  :stop (disconnect-db! db-connection))
```

### Pitfall 4: Lost REPL History

**Solution**: Use `.clojure/repl-history` or editor features

```clojure
;; Add to ~/.clojure/deps.edn
{:aliases
 {:repl
  {:extra-deps {reply/reply {:mvn/version "0.5.1"}}
   :main-opts ["-m" "reply.main"]}}}
```

## Complete Example: REPL-Driven Feature Development

**Goal**: Build a user authentication system

```clojure
(ns myapp.auth
  (:require [buddy.hashers :as hashers]
            [clojure.spec.alpha :as s]))

;; 1. Define specs for data validation
(s/def ::email (s/and string? #(re-matches #".+@.+\..+" %)))
(s/def ::password (s/and string? #(>= (count %) 8)))
(s/def ::user (s/keys :req-un [::email ::password]))

(comment
  ;; Test specs interactively
  (s/valid? ::email "user@example.com")  ; => true
  (s/valid? ::email "invalid")           ; => false
  (s/explain ::user {:email "test@test.com" :password "short"})
  :rcf)

;; 2. Build hash-password function
(defn hash-password [password]
  (hashers/derive password))

(comment
  (def hashed (hash-password "mysecret123"))
  hashed
  ;; => "bcrypt+sha512$4i9sd..."

  ;; Test verification
  (hashers/check "mysecret123" hashed)  ; => true
  (hashers/check "wrongpass" hashed)    ; => false
  :rcf)

;; 3. Create user registration
(defn register-user [db user-data]
  (when (s/valid? ::user user-data)
    (let [hashed-pwd (hash-password (:password user-data))
          user (assoc user-data :password hashed-pwd)]
      (save-user! db user))))

(comment
  ;; Mock database for testing
  (def mock-db (atom {}))

  (defn save-user! [db user]
    (swap! db assoc (:email user) user))

  ;; Test registration flow
  (register-user mock-db
                 {:email "alice@example.com"
                  :password "secure123"})

  @mock-db
  ;; => {"alice@example.com" {:email "..." :password "bcrypt+..."}}

  :rcf)

;; 4. Build authentication function
(defn authenticate [db email password]
  (when-let [user (get @db email)]
    (when (hashers/check password (:password user))
      (dissoc user :password))))

(comment
  ;; Test authentication
  (authenticate mock-db "alice@example.com" "secure123")
  ;; => {:email "alice@example.com"}

  (authenticate mock-db "alice@example.com" "wrongpass")
  ;; => nil

  (authenticate mock-db "nobody@example.com" "anypass")
  ;; => nil

  :rcf)

;; 5. Now write formal tests
(ns myapp.auth-test
  (:require [clojure.test :refer [deftest is testing]]
            [myapp.auth :as auth]))

(deftest authentication-test
  (let [db (atom {})]
    (testing "user registration"
      (auth/register-user db {:email "test@example.com"
                              :password "secure123"})
      (is (contains? @db "test@example.com")))

    (testing "successful authentication"
      (is (= {:email "test@example.com"}
             (auth/authenticate db "test@example.com" "secure123"))))

    (testing "failed authentication"
      (is (nil? (auth/authenticate db "test@example.com" "wrongpass"))))))
```

## Best Practices Summary

### DO:
- ✅ **Start REPL first**: Launch before writing code
- ✅ **Evaluate continuously**: Test every function immediately
- ✅ **Use rich comments**: Document explorations inline
- ✅ **Build bottom-up**: Small functions → composition
- ✅ **Manage state**: Use mount/integrant/component
- ✅ **Inspect data**: Use Portal, tap>, CIDER inspector
- ✅ **Write tests after**: Codify successful REPL experiments
- ✅ **Reload carefully**: Use refresh, avoid stale state
- ✅ **Use 1.12 features**: Method values, qualified methods
- ✅ **Keep REPL running**: Long sessions with state management

### DON'T:
- ❌ **Write without REPL**: Don't code in a vacuum
- ❌ **Batch evaluation**: Don't wait to test everything at once
- ❌ **Side effects at top**: Avoid execution on namespace load
- ❌ **Ignore state**: Manage component lifecycle explicitly
- ❌ **Lose experiments**: Capture in rich comments or design journals
- ❌ **Skip tests**: REPL-driven ≠ test-less
- ❌ **Circular deps**: Structure namespaces carefully
- ❌ **Complex expressions**: Keep evaluation units small
- ❌ **Manual reloads**: Automate with tools
- ❌ **Fear the REPL**: It's your friend, not intimidating

This skill enables the highly productive, interactive development style that makes Clojure unique and powerful.