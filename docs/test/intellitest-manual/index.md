---
title: IntelliTest-Referenzleitfaden | Testtools für Microsoft-Entwickler
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
  - 'IntelliTest Reference Manual, IntelliTest'
ms.author: gewarren
manager: jillfra
ms.workload:
  - multiple
author: gewarren
---
# <a name="intellitest-reference-manual"></a>IntelliTest-Referenzhandbuch

## <a name="contents"></a>Inhalt

* **[Übersicht über IntelliTest](introduction.md)**
  - [Das „Hello World“ von IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Einschränkungen](introduction.md#limitations)
    * [Nichtdeterminiertheit](introduction.md#nondeterminism)
    * [Parallelität](introduction.md#concurrency)
    * [Nativer Code](introduction.md#native-code)
    * [Plattform](introduction.md#platform)
    * [Sprache](introduction.md#language)
    * [Symbolischer Ansatzpunkt](introduction.md#symbolic-reasoning)
    * [Falsche Stapelüberwachungen](introduction.md#incorrect-stack-traces)
  - [Weiterführende Themen](introduction.md#further-reading)

* **[Erste Schritte mit IntelliTest](getting-started.md)**
  - [Wichtige Attribute](getting-started.md#important-attributes)
  - [Wichtige statische Hilfsklassen](getting-started.md#helper-classes)

* **[Testerzeugung](test-generation.md)**
  - [Testgeneratoren](test-generation.md#test-generators)
  - [Parametrisierte Komponententests](test-generation.md#parameterized-unit-testing)
  - [Generische parametrisierte Komponententests](test-generation.md#generic-parameterized)
  - [Zulassen von Ausnahmen](test-generation.md#allowing-exceptions)
  - [Testen von interne Typen](test-generation.md#internal-types)
  - [Annahmen und Assertionen](test-generation.md#assumptions-and-assertions)
  - [Vorbedingung](test-generation.md#precondition)
  - [Nachbedingung](test-generation.md#postcondition)
  - [Fehlgeschlagenen Tests](test-generation.md#test-failures)
  - [Einrichtung und Löschung](test-generation.md#setup-teardown)
  - [Weiterführende Themen](test-generation.md#further-reading)

* **[Eingabeerzeugung](input-generation.md)**
  - [Einschränkungs-Solver](input-generation.md#constraint-solver)
  - [Dynamische Codeabdeckung](input-generation.md#dynamic-code-coverage)
  - [Integer und float-Eigenschaften](input-generation.md#integers-and-floats)
  - [Objekte](input-generation.md#objects)
  - [Instanziieren vorhandener Klassen](input-generation.md#existing-classes)
  - [Sichtbarkeit](input-generation.md#visibility)
  - [Parametrisierte Mocks](input-generation.md#parameterized-mocks)
  - [Strukturen](input-generation.md#structs)
  - [Arrays und Zeichenfolgen](input-generation.md#arrays-and-strings)
  - [Abrufen von zusätzlichen Eingaben](input-generation.md#additional-inputs)
  - [Weiterführende Themen](input-generation.md#further-reading)

* **[Explorationsgrenzen](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)

* **[Attribute Glossary](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)

* **[Einstellungswasserfall](settings-waterfall.md)**

* **[Statische Hilfsklassen](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[Warnungen und Fehler](warnings-and-errors.md)**
  - [MaxBranches überschritten](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime überschritten](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions überschritten](warnings-and-errors.md#maxconditions-exceeded)
  - [MaxCalls überschritten](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack überschritten](warnings-and-errors.md#maxstack-exceeded)
  - [MaxRuns überschritten](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests überschritten](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Die Lösung kann nicht konkretisiert werden](warnings-and-errors.md#cannot-concretize-solution)
  - [Benötigen Sie Hilfe bei der Objekterstellung?](warnings-and-errors.md#help-construct)
  - [Benötigen Sie Hilfe beim Suchen von Typen?](warnings-and-errors.md#help-types)
  - [Verwendbaren Typ erraten](warnings-and-errors.md#usable-type-guessed)
  - [Unerwarteter Fehler während der Erforschung](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Nicht instrumentierte aufgerufene Methode](warnings-and-errors.md#uninstrumented-method-called)
  - [Externe aufgerufene Methode](warnings-and-errors.md#external-method-called)
  - [Nicht instrumentierbare aufgerufene Methode](warnings-and-errors.md#uninstrumentable-method-called)
  - [Probleme mit der Testfähigkeit](warnings-and-errors.md#testability-issue)
  - [Einschränkung](warnings-and-errors.md#limitation)
  - [Erkannter Aufrufkonflikt](warnings-and-errors.md#observed-call-mismatch)
  - [Im Feld „static“ gespeicherten Wert](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>Sie möchten Feedback geben?

Posten Sie Ihre Ideen und Featureanfragen in der [Entwicklercommunity](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).