---
title: "IntelliTest-Referenzhandbuch | Testtools für Microsoft-Entwickler | Microsoft-Dokumentation"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest Reference Manual, IntelliTest
ms.assetid: C5FA1C59-BB82-43B6-BF96-D0D85E033DAE
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 300f2a830b2bd22c39798821cfd6cd8e804fb64a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="intellitest-reference-manual"></a>IntelliTest-Referenzhandbuch

## <a name="contents"></a>Inhalt

* **[Übersicht über IntelliTest](introduction.md)**
  - [Das „Hello World“ von IntelliTest](introduction.md#hello-world)
  - [Einschränkungen](introduction.md#limitations)
    * [Nichtdeterminiertheit](introduction.md#nondeterminism)
    * [Parallelität](introduction.md#concurrency)
    * [Nativer Code](introduction.md#native-code)
    * [Plattform](introduction.md#platform)
    * [Sprache](introduction.md#language)
    * [Symbolischer Ansatzpunkt](introduction.md#symbolic-reasoning)
    * [Falsche Stapelüberwachungen](introduction.md#incorrect-stack)
  - [Weiterführende Themen](introduction.md#further-reading)<p>&nbsp;</p>

* **[Erste Schritte mit IntelliTest](getting-started.md)**
  - [Wichtige Attribute](getting-started.md#important-attributes)
  - [Wichtige statische Hilfsklassen](getting-started.md#helper-classes)<p>&nbsp;</p>
 
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
  - [Weiterführende Themen](test-generation.md#further-reading)<p>&nbsp;</p>

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
  - [Weiterführende Themen](input-generation.md#further-reading)<p>&nbsp;</p>

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
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)<p>&nbsp;</p>

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
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)<p>&nbsp;</p>

* **[Einstellungswasserfall](settings-waterfall.md)**

* **[Statische Hilfsklassen](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)<p>&nbsp;</p>

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
  - [Im Feld „static“ gespeicherten Wert](warnings-and-errors.md#value-static-field)<p>&nbsp;</p>

## <a name="got-feedback"></a>Sie möchten Feedback geben?

Posten Sie Ihre Ideen und Clusterfunktion Anforderungen auf **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
