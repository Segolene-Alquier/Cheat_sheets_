# Testing_rails

Ecrire les tests avant de coder peut sembler fastidieux car rajoute du code supplémentaire, mais c'est en fait souvent un gain de temps qui permet d'anticiper de futurs bugs et d'écrire du code plus clean.

Les avantages :
* aide à prévoir les comportements de l'application
* aide à protéger les applications de régressions avec le développement d'évolutions
* permet d'avoir plus confiance en son code pour le refactor

Quand écrire les tests avant de développer les fonctions ?
* Quand un test est particulièrement court ou simple comparé à l'application testée
* Quand le résultat désiré n'est pas très clair
* Dès qu'un bug est déclaré, il est possible d'écrire un test pour le reproduire et ainsi le réparer
* Pour des parties de code qui risquent de changer ultérieurement
* ...

> On utilisera sur Rails majoritairement les 'controller tests', les 'model tests' et les 'integration tests'

Les TDD (Test Driven Devlopment) impliquent d'écrire un test d'échec en premier, puis d'écrire le code nécessaire pour passer le test

## Les frameworks de test

Il existe des gems et des librairies de test sur Rails

### RSpec vs MiniTest
#### MiniTest
Dans les dernières versions de Rails, le framework de testing inclus par défaut est MiniTest.

##### Les assertions
Assertion	| Purpose
----------|---------
assert( test, [msg] )	| Ensures that test is true.
assert_not( test, [msg] )	| Ensures that test is false.
assert_equal( expected, actual, [msg] )	| Ensures that expected == actual is true.
assert_not_equal( expected, actual, [msg] )	| Ensures that expected != actual is true.
assert_same( expected, actual, [msg] ) |	Ensures that expected.equal?(actual) is true.
assert_not_same( expected, actual, [msg] )	| Ensures that expected.equal?(actual) is false.
assert_nil( obj, [msg] )	| Ensures that obj.nil? is true.
assert_not_nil( obj, [msg] )	| Ensures that obj.nil? is false.
assert_empty( obj, [msg] )	| Ensures that obj is empty?.
assert_not_empty( obj, [msg] )	| Ensures that obj is not empty?.
assert_match( regexp, string, [msg] )	| Ensures that a string matches the regular expression.
assert_no_match( regexp, string, [msg] )	| Ensures that a string doesn't match the regular expression.
assert_includes( collection, obj, [msg] )	| Ensures that obj is in collection.
assert_not_includes( collection, obj, [msg] )	| Ensures that obj is not in collection.
assert_in_delta( expected, actual, [delta], [msg] )	| Ensures that the numbers expected and actual are within delta of each other.
assert_not_in_delta( expected, actual, [delta], [msg] )	| Ensures that the numbers expected and actual are not within delta of each other.
assert_throws( symbol, [msg] ) { block }	| Ensures that the given block throws the symbol.
assert_raises( exception1, exception2, ... ) { block }	| Ensures that the given block raises one of the given exceptions.
assert_instance_of( class, obj, [msg] )	| Ensures that obj is an instance of class.
assert_not_instance_of( class, obj, [msg] ) |	Ensures that obj is not an instance of class.
assert_kind_of( class, obj, [msg] )	| Ensures that obj is an instance of class or is descending from it.
assert_not_kind_of( class, obj, [msg] )	| Ensures that obj is not an instance of class and is not descending from it.
assert_respond_to( obj, symbol, [msg] )	| Ensures that obj responds to symbol.
assert_not_respond_to( obj, symbol, [msg] )	| Ensures that obj does not respond to symbol.
assert_operator( obj1, operator, [obj2], [msg] )	| Ensures that obj1.operator(obj2) is true.
assert_not_operator( obj1, operator, [obj2], [msg] )	| Ensures that obj1.operator(obj2) is false.
assert_predicate ( obj, predicate, [msg] )	| Ensures that obj.predicate is true, e.g. assert_predicate str, :empty?
assert_not_predicate ( obj, predicate, [msg] )	| Ensures that obj.predicate is false, e.g. assert_not_predicate str, :empty?
flunk( [msg] )	| Ensures failure. This is useful to explicitly mark a test that isn't finished yet.

Le paramètre [msg] est optionnel (format string). Il permet d'éclaircir les raisons d'un échec de test

Pour plus d'assertions sur MiniTest : http://docs.seattlerb.org/minitest/Minitest/Assertions.html

##### Le test runner

Pour lancer tous les tests en même temps : ```$ rails test```

Pour lancer un seul test : ```$ rails test /FILENAME.rb```

Pour lancer une seule ligne d'un test : ```$ rails test /FILENAME.rb:6```



#### RSpec

RSpec est une alternative intéressante est la structure ressemble à cela :
```
describe “the test” do
  it “is a success” do
    expect(1).to eq(1)
  end
end
```

## Les différents types de tests

![Types](https://image.noelshack.com/fichiers/2018/07/1/1518434309-capture-d-ecran-2018-02-12-a-12-15-55.png "differents test")
