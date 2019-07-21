:title: WebAssembly
:data-transition-duration: 1500

----

WebAssembly
===========

Alexander Koch
01.08.2018

----

WebAssembly
===========

WebAssembly (Wasm) ist
 * ein Binärformat für eine stapelbasierte Virtuelle Maschine
 * portierbarer Zielcode für Kompilation von Hochsprachen
 * geeignet für Client- und Serveranwendungen
 
----

Warum
===========

JavaScript Unterstützung im Browser wird immer bessser, besonders mit
threading (pthreads) und verbesserten numerischen Operationen (SIMD).  

Warum jetzt noch WebAssembly?

.. class:: substep

1. Das Binärformat kann nativ bis zu 20x schneller dekodiert werden als JavaScript

2. Vermeidet Beschränkungen der AoT Kompatibilität, erlaubt dadurch Optimierungen einfach um zu setzen um native Perfomance zu erreichen  

----

Ziele
===========

 * portables Binärformat, optimiert auf Größe und Ladezeit das native Geschwindigkeit erreichne soll
 * MVP mit Funktionsumfang ähnlich *asm.js* und C/C++ als unterstützte Sprache 
 * nahtlose Einbindung in die Web Platform, JavaScript Andindung, Sicherheitsfeatures von Webbroswern etc
 * Unterstützung für Einbetttung auch ohne Browser
 * mächtige Toolchain, LLVM Backend, einfache Anbindung anderer Compiler/Toolchains 

----

Anwendungsfälle
===============
 * bessere Ausführung cross-compilierter Toolkits (C/C++, GWT)
 * Bild- und Videobearbeitung
 * Spiele
 * AI und VR, AR
 * CAD
 * Remote Desktop
 * VPN, Verschlüsselung
 * Developer tooling, virtuelle Maschinen, Interpreter
 * ... 

----

Geschichte
===========

 * April 2015 - WebAssembly Community Group startet (eine W3C Gruppe)
 * Juni 2015 - Erste öffenliche Ankündigung
 * März 2016 - Festlegung der Kernfunktionalität
 * Oktober 2016 - Browser Preview mit verschiedenen, interoperablen Implementierungen
 * März 2017 - Cross-browser Konsens erreicht, Ende der Browser Preview

----

Umsetzung
===========

WebAssembly CG (Chrome, Edge, Firefox, and WebKit) sehen intialen MVP und Binärformat als komplett an

 * API, JavaScrip API und Binärformat kompleet
 * Ende der "Browser Preview", Auslieferunf kann beginnen mit "on-by-default"
 * künftige Änderungen und Erweiterungen müssen abwärtskompatibel sein 

WebAssembly läuft in einer Sandbox im Browser, ähnlich JavaScript

----

Ausblick
=========== 
 * einheitliche Spezifikation bereitstellen
 * neue Charta für die W3C WebAssembly Working Group erstellen
 * das WebAssemble LLVM Backend von experimentell auf stabil bringen 
 * post-MVP Funktionalität umsetzen (Threads, SIMD, GC, Type Reflection, Bulk Memory Operations ...)
 
----

Umsetzung
===========

Design Komponenten
 * module: eine auslieferbare, ladbare, ausführbare Code-Einheit
 * instructions: das Verhalten in einem Modul wird durch Anweisungen für eine stapelbasierte Maschine
 * binary encoding: Struktur und Code eines Moduls werden mittels der Binärcodierung in einem Binärformat abgebildet
 * text format: eine textuelle Projektion von Struktur und Code eines Moduls
 * Web browsers und execution environments: Ziel für die Implementierung von WebAssembly   

----

Tools / Toolchains
==================

Unterstützung für rohes Wasm Format:
 * WABT (The WebAssembly Binary Toolkit) konvertiert zwischen dem Binär- und dem Textformat
 * Binaryen - Unterstützung für Compiler and toolchain infrastructure, mit C API

Toolschains:
 * emscripten: LLVM basierte Toolchain um C/C++ nach asm.js und WebAssembly zu kompilieren
 * wasm-pack: Rust toolchain
 * wasm_exex.js für Go: "glue" für Webassembly und Go
 * Kotline Native: unterstützt WebAssembly

----

Stand heute
===========

86.92% der Browser unterstützen Wasm (Quelle https://caniuse.com/#feat=wasm 21.07.2019)

 * aktuell nur vier numerische Datentypen (32- und 64-Bit-Integer, 32 und 64 Bit Float)
 * noch keine Garbage Collection
 * noch keine direkte Interaktion mit DOM und anderen Browser APIs
 * benötigt JavaScript zur Initalisierung und Interaktion mit Browser APIs

----

WASM mit Kotlin/Native
======================



----
* https://webassembly.org/
* https://webassembly.github.io/spec/core/index.html
* https://superkotlin.com/kotlin-and-webassembly/
* https://jaxenter.de/enterprisetales-webassembly-78989
