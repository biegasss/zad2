# Lekcja 1 – Markdown lekki język znaczników



# Spis treści

[toc]

## Wstęp

Obecnie powszechnie wykorzystuje się języki ze znacznikami do opisania dodatkowych informacji
umieszczanych w plikach tekstowych. Z pośród najbardziej popularnych można wspomnieć o:

1. **html** – służącym do opisu struktury informacji zawartych na stronach internetowych,
2. **Tex** (Latex) – poznany na zajęciach język do „profesjonalnego” składania tekstów,
3. **XML** (Extensible Markup Language) - uniwersalnym języku znaczników przeznaczonym do
   reprezentowania różnych danych w ustrukturalizowany sposób.

Przykład kodu html i jego interpretacja w przeglądarce:

&lt;!DOCTYPE **html**&gt;
&lt;**html**&gt;
&lt;**head**&gt;
&lt;**meta** <span style="color:blue">charset</span><span style="color:green">=</span><span style="color:red">"utf-8"</span> <span style="color:green">/</span>&gt;
&lt;<span style="color:blue">title</span>&gt;Przykład&lt;/<span style="color:blue">title</span>&gt;
&lt;<span style="color:green">/</span>**head**&gt;
&lt;**body**&gt;
&lt;**p**&gt; Jakiś paragraf tekstu&lt;<span style="color:green">/</span>**p**&gt;
&lt;<span style="color:green">/</span>**body**&gt;
&lt;<span style="color:green">/</span>**html**&gt;

![alttext](https://i.ibb.co/WHv6PxJ/obraz-1.jpg "obraz 1")

Przykład kodu Latex i wygenerowanego pliku w formacie pdf

&#8726;<span style="color:brown">documentclass</span>[]{<span style="color:blue">letter</span>}
&#8726;<span style="color:brown">usepackage</span>{<span style="color:blue">lipsum</span>}
&#8726;<span style="color:brown">usepackage</span>{<span style="color:blue">polyglossia</span>}
&#8726;<span style="color:brown">setmainlanguage</span>{<span style="color:blue">polish</span>}
&#8726;<span style="color:blue">**begin**</span>{<span style="color:blue">**document**</span>}
&#8726;<span style="color:blue">**begin**</span>{<span style="color:blue">**letter**</span>}{<span style="color:blue">**Szanowny Panie XY**</span>}
&#8726;<span style="color:brown">address</span>{<span style="color:blue">Adres do korespondencji</span>}
&#8726;<span style="color:brown">opening</span>{}
&#8726;<span style="color:brown">lipsum</span>[2]
&#8726;<span style="color:brown">signature</span>{<span style="color:blue">Nadawca</span>}
&#8726;<span style="color:brown">closing</span>{<span style="color:blue">Pozdrawiam</span>}
&#8726;<span style="color:blue">**end**</span>{<span style="color:blue">**letter**</span>}
&#8726;<span style="color:blue">**end**</span>{<span style="color:blue">**document**</span>}

![alttext](https://i.ibb.co/YyDJmTh/obraz-2.jpg "obraz 2")

Przykład kodu XML – fragment dokumentu SVG (Scalar Vector Graphics)

&lt;!DOCTYPE **html**&gt;
&lt;**html**&gt;
&lt;**body**&gt;
&lt;svg <span style="color:blue">height</span><span style="color:green">=</span> <span style="color:red">"100"</span> <span style="color:blue">width</span><span style="color:green">=</span><span style="color:red">"100"</span>&gt;
&lt;circle cx<span style="color:green">=</span><span style="color:red">"50"</span> cy<span style="color:green">=</span><span style="color:red">"50"</span> r<span style="color:green">=</span><span style="color:red">"40"</span> stroke<span style="color:green">=</span><span style="color:red">"black" </span>stroke-<span style="color:blue">width</span><span style="color:green">=</span><span style="color:red">"3"</span> fill<span style="color:green">=</span><span style="color:red">"red"</span> /&gt;
&lt;<span style="color:green">/</span>svg&gt;
&lt;<span style="color:green">/</span>**body**&gt;
&lt;<span style="color:green">/</span>**html**&gt;

![alttext](https://i.ibb.co/9VYFGSX/obraz-3.jpg "obraz 3")

W tym przypadku mamy np. znacznik np. &lt;circle&gt; opisujący parametry koła i który może być
właściwie zinterpretowany przez dedykowaną aplikację (np. przeglądarki www).
Jako ciekawostkę można podać fakt, że również pakiet MS Office wykorzystuje format XML do
przechowywania informacji o dodatkowych parametrach formatowania danych. Na przykład pliki z
rozszerzeniem _docx_, to nic innego jak spakowane algorytmem zip katalogi z plikami xml.

<span style="color:green">$unzip</span> -l <span style="color:#9900cc">test</span>.docx
Archive: <span style="color:#9900cc">test</span>.docx
Length <span style="color:Fuchsia">Date</span> **Time** Name

&minus;&minus;&minus;&minus;&minus;&minus;&minus;&minus;&minus;   &minus;&minus;&minus;&minus;&minus;&minus;&minus;&minus;&minus;&minus;  &minus;&minus;&minus;&minus;&minus;  &minus;&minus;&minus;&minus;

573 2020-10-11 18:20 _rels/.rels
731 2020-10-11 18:20 docProps/core.xml
508 2020-10-11 18:20 docProps/app.xml
531 2020-10-11 18:20 word/_rels/document.xml.rels
1421 2020-10-11 18:20 word/document.xml
2429 2020-10-11 18:20 word/styles.xml
853 2020-10-11 18:20 word/fontTable.xml
241 2020-10-11 18:20 word/settings.xml
1374 2020-10-11 18:20 [Content_Types].xml

Wszystkie te języki znaczników cechują się rozbudowaną i złożoną składnią i dlatego do ich edycji
wymagają najczęściej dedykowanych narzędzi w postaci specjalizowanych edytorów. By
wyeliminować powyższą niedogodność powstał **Markdown** - uproszczony język znaczników
służący do formatowania dokumentów tekstowych (bez konieczności używania specjalizowanych
narzędzi). Dokumenty w tym formacie można bardzo łatwo konwertować do wielu innych
formatów: np. html, pdf, ps (postscript), epub, xml i wiele innych. Format ten jest powszechnie
używany do tworzenia plików README.md (w projektach open source) i powszechnie
obsługiwany przez serwery git’a. Język ten został stworzony w 2004 r. a jego twórcami byli John
Gruber i Aaron Swartz. W kolejnych latach podjęto prace w celu stworzenia standardu rozwiązania
i tak w 2016 r. opublikowano dokument [RFC 7764](https://tools.ietf.org/html/rfc7764) który zawiera opis kilku odmian tegoż języka:

* CommonMark,
* GitHub Flavored Markdown (GFM),
* Markdown Extra.



## Podstawy składni

Podany link: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet zawiera opis
podstawowych elementów składni w języku angielskim. Poniżej zostanie przedstawiony ich krótki
opis w języku polskim.



### Definiowanie nagłówków

W tym celu używamy znaku kratki

Lewe okno zawiera kod źródłowy – prawe -podgląd przetworzonego tekstu

![alttext](https://i.ibb.co/MGJCqDM/obraz-4.jpg "obraz 4")

### Definiowanie list



![alttext](https://i.ibb.co/n8B3KsP/obraz-5.jpg "obraz 5")

Listy numerowane definiujemy wstawiając numery kolejnych pozycji zakończone kropką.

Listy nienumerowane definiujemy znakami: *,+,-



### Wyróżnianie tekstu



![alttext](https://i.ibb.co/0XQqM41/obraz-6.jpg "obraz 6")

### Tabele



![alttext](https://i.ibb.co/mC66d71/obraz-7.jpg "obraz 7")

Centrowanie zawartości kolumn realizowane jest poprzez odpowiednie użycie znaku dwukropka:



### Odnośniki do zasobów

&#91;odnośnik do zasobów&#93;(www.gazeta.pl)

&#91;odnośnik do pliku](LICENSE.md)

&#91;odnośnik do kolejnego zasobu][1]

&#91;1&#93;: http://google.com

### Obrazki

!&#91;alt text&#93;(https://server.com/images/icon48.png "Logo 1") – obrazek z zasobów
internetowych
!&#91;&#93;(logo.png) – obraz z lokalnych zasobów

### Kod źródłowy dla różnych języków programowania



![alttext](https://i.ibb.co/NF1fph5/obraz-8.jpg "obraz 8")

### Tworzenie spisu treści na podstawie nagłówków



![alttext](https://i.ibb.co/m6bwnVS/obraz-9.jpg "obraz 9")

## Edytory dedykowane



Pracę nad dokumentami w formacie Markdown( rozszerzenie md) można wykonywać w dowolnym edytorze tekstowym. Aczkolwiek istnieje wiele dedykowanych narzędzi

1. Edytor Typora - https://typora.io/
2. Visual Studio Code z wtyczką „markdown preview”

![alttext](https://i.ibb.co/bQPv8wh/obraz-10.jpg "obraz 10")

## Pandoc – system do konwersji dokumentów Markdown do innych formatów



Jest oprogramowanie typu open source służące do konwertowania dokumentów pomiędzy różnymi formatami.

Pod poniższym linkiem można obejrzeć przykłady użycia:

https://pandoc.org/demos.html

Oprogramowanie to można pobrać z spod adresu: https://pandoc.org/installing.html

Jeżeli chcemy konwertować do formatu latex i pdf trzeba doinstalować oprogramowanie składu Latex (np. Na windows najlepiej sprawdzi się Miktex https://miktex.org/)

Gdyby podczas konwersji do formatu pdf pojawił się komunikat o niemożliwości znalezienia programu pdflatex rozwiązaniem jest wskazanie w zmiennej środowiskowej PATH miejsca jego położenia

![alttext](https://i.ibb.co/WyZZhcV/obraz-11.jpg "obraz 11")

![alttext](https://i.ibb.co/vqyf23J/obraz-12.jpg "obraz 12")

![alttext](https://i.ibb.co/NmBzmp3/obraz-13.jpg "obraz 13")

Pod adresem (https://gitlab.com/mniewins66/templatemn.git) znajduje się przykładowy plik Markdown z którego można wygenerować prezentację w formacie pdf wykorzystując klasę latexa beamer.

W tym celu należy wydać polecenie z poziomu terminala:

$pandoc templateMN.md -t beamer -o prezentacja.pdf