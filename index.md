---
layout: default
title: Frameworki js i json
---
# Frameworki js i json
## Temat
* Trend będący na styku aplikacji mobilnych i stron internetowych
* Korzysta z wszechobecności js i prostoty json
* Bardzo istotna tendecja - prawdopodobnie doprowadzi że do tego że wkrótce wiele związanego z internetem kodu będzie powstawać w js

## Kim jestem?
* Marcin Wosinek
* 5 lat doświadczenia w IT
 * WebDev: Javascript
 * C# dev: UnitTests
* Aktualnie js kontraktor z Poznaniu

## Wy?
* Kto tworzy strony internetowe?
* Kto lubi js?
* Kto zgadza się ze stwierdzeniem "unit testy to istotna częśc rzemiosła programistycznego"
* Kto pisze testy?
 * Racja - pisanie testów dla jQuerowej kluchy to ból: więc dzisiaj przyjżymy się bardziej testowalnemu podejściu
* Zapraszam do zadawania pytań - w trakcie i po prezentacji

## Jak działają strony internetowe?
* serwer generuje html z danych za pomocą templatów serwerowych
* dana, obciążone html są wysyłane do przeglądarki
* w js robimy proste operacje na dokumencie wygenerowanym po stronie serwera

## Na ogół jest inaczej 
* aplikacja jest na po stronie klienta
* serwer wystawia DANE
* widoki sa generowane po stronie klienta

## Czemu internet był inny?
* brak dojrzałej, powszechnej technologii - javascript, flash, silverlight i aplety java
* brak gotowości front endu na zwiększenie zakresu odowiedzialności
* brak stosowanie dobrych praktyk:
 * testów
 * wzorców projektowych

## Ale js?
* js to nie tylko jQuery z pluginami 
* jest możliwe w wygodny sposób korzystać z dobrych praktyk programistycznych w js

## Js wygrał i jest gotowy!
* urządzenia mobilne nie wspierają silverlighta i flasha - i tym samy obie technologie wypadły z gry
* mało kto pamięta o apletach java

## Aplikacje js
* cześć logiki trafia do przeglądarek
* wymagają włączonego js
* pozwalają na bardziej rozbudowane i wygodniejsze interfejsy

## Kiedy stosować aplikacje
* Wtedy kiedy użytkownik jest po zalogowaniu
* W intranetowych zastosowaniach
* W reszcie przypadków dobrze mieć fallback dla bez jsowych user-agentów i botów wyszukiware

## Frameworki JS

* Dostarczają architektury
* Umożliwiają zwiększanie zakresu obowiązków front endu
* Bardzo duży wybór
* jQuery nie jest frameworkiem

## JSON
* format serializowania objektów
* json - bardzo prosta i naturalna składnia
* podobne konstrukcje występują w innych językach

```js
{
  "menu": {
    "id": "file",
    "value": "File",
    "popup": {
      "menuitem": [
        { "value": "New", "href": "#createNewDoc" },
        { "value": "Open", "href": "#openDoc" },
        { "value": "Close", "href": "#closeDoc" }
      ]
    }
  }
}
```

## JSON vs XML
* xml - potrzeba bibliotek do parsowania
* xml - złożona składnia, wiele sposóbów na przedstwienie tego samego

```xml
<person first-name="John" last-name="Smith"/>

<person>
  <first-name>John</first-name>
  <last-name>Smith</last-name>
</person>

<object type="Person">
  <property name="first-name">John</property>
  <property name="last-name">Smith</property>
</object>
```

```js
{
  "first-name": "John",
  "last-name": "Smith" 
}
```
(źródło http://blog.mongolab.com/2011/03/why-is-json-so-popular-developers-want-out-of-the-syntax-business/)

## Rest vs soap
* soap w javascripcie jest bolesny
* rest + json są bardzo naturalne w js
Soap:

```js
function soap() {
    var xmlhttp = new XMLHttpRequest();
    xmlhttp.open('POST', 'https://somesoapurl.com/', true);

    // build SOAP request
    var sr =
        '<?xml version="1.0" encoding="utf-8"?>' +
        '<soapenv:Envelope ' + 
            'xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" ' +
            'xmlns:api="http://127.0.0.1/Integrics/Enswitch/API" ' +
            'xmlns:xsd="http://www.w3.org/2001/XMLSchema" ' +
            'xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">' +
            '<soapenv:Body>' +
                '<api:some_api_call soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">' +
                    '<username xsi:type="xsd:string">login_username</username>' +
                    '<password xsi:type="xsd:string">password</password>' +
                '</api:some_api_call>' +
            '</soapenv:Body>' +
        '</soapenv:Envelope>';

    xmlhttp.onreadystatechange = function () {
        if (xmlhttp.readyState == 4) {
            if (xmlhttp.status == 200) {

                alert('done use firebug to see responce');
            }
        }
    }
    // Send the POST request
    xmlhttp.setRequestHeader('Content-Type', 'text/xml');
    xmlhttp.send(sr);
    // send request
    // ...
}
```
(source: http://stackoverflow.com/a/11404133/603544)

## Angular
* Framework js
 * 29KB zminimalizowany i spakowany
 * backbone: 19KB (z underscore & zepto)
 * backbone: 32KB (z lodash & jQuery)
 * ember: 49KB
* brak zależności:
 * może używać jQuery, o ile jest dostępne przy uruchomieniu

## Angular: MV*
* W kontrolerze opisujemy krok po kroku logike (imperatywnie)
* W widoku odwołujemy się do elementów zdefiniowanych w kontrolerze (deklaratywnie)
* $scope scala jedno i drugie razem

## AngularJs: two ways binding
* Dwu stronne powiązanie modelu z widokiem
* Bardzo szybkie
* opartę o proste porównywanie wartości

### Demonstracja! - strona http://angularjs.org/
* Mega prosty kod - bardzo przyjemna funkcjonalność

## Angular: rozszerzanie html
* Directives - angularowy sposób na łączenie html z js
* Controller nie tyka DOM
* Programowanie deklaratyne

```html
<div ng-controller="ProductCtrl">

<ul>
  <li ng-repeat="friend in friends">
    [{ {$index + 1}}] { {friend.name}} who is { {friend.age}} yrs old.
  </li>
</ul>

<input type="checkbox" ng-model="confirmed" ng-change="change()" />

<blink>Click me</blink>

```

## Angular: wstrzykiwanie zależności
* ładny sposób na podsumowanie z czym integruje się dany kawałek kodu
* pozwala na kontrolować z czego korzystają instancje funkcji - prawdziwych obiektów, czy mocków

```js
$scope; // view model
$log; // konsola: przyjazna dla ie
$window; // Testowalny odpowiednik window
$http; // requesty http
// wszystkie nasze serwisy

/*----------*/

function TodoCtrl($scope, $log) {
  $scope.addTodo = function() {
    $log.log($scope.msg);
    $scope.msg = "";
  };
};
```

## Angular: testowalność
* Brak manipulacji DOM w kotrolerach
* Wstrzykiwanie zależności
* Wysoka testowalność, czyniąca TDD możliwym i przyjemnym

```js
function PasswordCtrl($scope) {
  $scope.password = '';
  $scope.grade = function() {
    var size = $scope.password.length;
    if (size > 8) {
      $scope.strength = 'strong';
    } else if (size > 3) {
      $scope.strength = 'medium';
    } else {
      $scope.strength = 'weak';
    }
  };
}

/*----------*/

var pc = new PasswordCtrl();
pc.password('abc');
pc.grade();
expect(pc.strength).toEqual('weak');
```

## Yeoman
* Zestaw narzędzi usprawniajacych pracę
 * wspiera angular, backbone, ember
* Zajmuje się nudnymi zadaniami
* wparcie dla sass, compass, coffeescript

## Yeoman: generowanie kodu
* W angularze elimuje część przegryzania się przez dokumentacje
* Usprawnia prace

## Yeoman: serwer testowy
* Obserwuje zmiany na plika; kompile co trzeba i puszuje do przeglądarki - bez f5

## Testacular
* test runner od teamu angularowego
* ładnie działa w TDD

## Podsumowanie
* Przeglądarkowy js jest bardzo szybko rozwijającą się gałęzią programowania
* Dobre praktyki z javy i rubego można sprawnie używać w js
* Json jest prostym formatem danych, idealnym w wielu przypadkach
* Warto poznać praktykę użycia trzech narzędzi razem: angular, testacular i yeoman

## Pytania?

1. Czemu angular a nie backbone?
2. Czy to podejścia da się zintegrować z legacy code?
3. Co walidatory na html dostosowany do angulara?
4. Z jakim backendem używać angulara?

## Warsztaty angularowe
kiedy: sobota, 23 marca, godzina 10.00
miejsce: WMiI UJ, sala 1160
rejestracja: rejestracja.ksi+js@gmail.com - podaj imię i nazwisko

## Gdzie można mnie złapać
marcin.wosinek@gmail.com
@MarcinWosinek
linki + notatki: http://marcin-wosinek.github.com/frameworki-js-i-json/
