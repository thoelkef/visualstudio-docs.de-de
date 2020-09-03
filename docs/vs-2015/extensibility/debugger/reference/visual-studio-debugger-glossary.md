---
title: Glossar für Visual Studio-Debugger | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 19d82f006bb1c37981f60e1a0b2710588eb0053c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204785"
---
# <a name="visual-studio-debugger-glossary"></a>Glossar zum Visual Studio-Debugger
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Im [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debuggingsdk werden die folgenden Begriffe verwendet:  
  
## <a name="terms"></a>Begriffe  
 gebundener Haltepunkt  
 Eine Abstraktion für einen Haltepunkt, der im Code festgelegt ist. Zwischen einem gebundenen Haltepunkt und einer breakpointanweisung im Codestream besteht eine eins-zu-eins-Beziehung. Wenn Code entladen wird, wird die Bindung gebundener Haltepunkte möglicherweise aufgehoben.  
  
 Kausalität  
 Bietet die Möglichkeit, einen logischen Ausführungs Thread über mehrere physische Threads, Prozesse und Computer hinweg zu verfolgen und die aufrufsliste dieses logischen Threads an einem beliebigen Punkt in der Lebensdauer des Threads zu rekonstruieren.  
  
 Codekontext  
 Stellt eine Abstraktion einer Position im Code bereit, der der Debug-Engine bekannt ist. Bei den meisten Lauf Zeit Architekturen ist ein Code Kontext eine Adresse im Anweisungs Datenstrom eines Programms. Bei nicht herkömmlichen Sprachen, in denen Code möglicherweise nicht durch Anweisungen dargestellt wird, kann ein Code Kontext auf andere Weise dargestellt werden.  
  
 Codepfad  
 Stellt einen Ausführungs Punkt in dem Code dar, in dem eine Verzweigung erstellt wird, oder ein Funktions Aufrufwert. Bei einer Stapel Überwachung handelt es sich im Wesentlichen um eine Liste von Code Pfaden für Funktionsaufrufe.  
  
 Debug-Engine (de)  
 Eine Komponente, die das Debuggen einer Lauf Zeit Architektur ermöglicht. Ein Debug-Modul funktioniert in Verbindung mit dem Interpreter oder dem Betriebssystem und stellt Debugdienste wie z. b. die Ausführungs Steuerung, Breakpoints und Ausdrucks Auswertung bereit.  
  
 Dokumentkontext  
 Stellt eine Abstraktion einer Position in einem Quelldatei Dokument bereit, das der Debug-Engine bekannt ist. In den meisten Sprachen ist ein Dokument Kontext eine Position in einer Quelldatei. Bei nicht herkömmlichen Sprachen, bei denen es sich bei der Quelldatei möglicherweise nicht um Text handelt, kann ein Dokument Kontext auf andere Weise dargestellt werden. Siehe auch *Dokument Position*.  
  
 Dokument Position  
 Stellt eine Abstraktion einer Position in einer Quelldatei bereit, die der IDE bekannt ist. In den meisten Sprachen ist eine Dokument Position eine Position in einer Quelldatei. Bei nicht herkömmlichen Sprachen kann eine Dokument Position auf andere Weise dargestellt werden. Siehe auch *Dokument Kontext*.  
  
 Fehler-Haltepunkt  
 Eine Abstraktion zum Beschreiben eines Fehlers in einem ausstehenden Breakpoint. Ein Fehler Haltepunkt kann einen Fehler am Speicherort des ausstehenden halte Punkts, den Ausdruck, der dem ausstehenden Haltepunkt zugeordnet ist, oder andere Informationen beschreiben, die verhindern, dass der ausstehende Haltepunkt an einen Code Speicherort gebunden wird.  
  
 Auswertungs Kontext  
 Stellt eine Abstraktion eines Programmier Kontexts für die Ausdrucks Auswertung bereit. In der Regel ist ein Auswertungs Kontext ein Bereich. Wenn die Ausdrucks Auswertung in einem Ausdrucks Kontext durchgeführt wird, stellt der Ausdrucks Kontext Bereichs Regeln bereit, die dem Zeitpunkt der Erstellung entsprechen. Ein Ausdrucks Kontext, der in einem Stapel Rahmen erstellt wurde, stellt z. b. den Kontext zum Auswerten von lokalen Variablen, Methoden Parametern, Klassenmembern (falls zutreffend) und globalen Variablen bereit.  
  
 abgefangene Ausnahme  
 Eine Ausnahme, die von einer Debug-Engine abgefangen wird, auch wenn kein Mechanismus zur Ausnahmebehandlung im aktuellen Stapel Rahmen vorhanden ist.  
  
 JustMyCode  
 Das Konzept, nur den Code zu debuggen, der einem Benutzer angehört, und den gesamten zwischen Code (z. b. Systemcode) zu ignorieren – auch wenn Quellcode für diesen Systemcode verfügbar ist.  
  
 ausstehender Haltepunkt  
 Stellt eine Abstraktion für Breakpoints vor, während und nach dem Laden von Code sowie eine Möglichkeit zum Virtualisieren von Breakpoints bereit. Ein ausstehender Haltepunkt:  
  
- Enthält alle Informationen, die erforderlich sind, um einen Breakpoint an Code in einem oder mehreren Programmen zu binden.  
  
- Kann an mehrere Code Speicherorte in einem oder mehreren Programmen gebunden werden.  
  
- Bindet sich niemals an den Code.  
  
  Jedes Mal, wenn Code geladen wird, werden alle ausstehenden Breakpoints in einem Programm geprüft, um festzustellen, ob Sie gebunden werden können. Ein ausstehender Haltepunkt enthält alle gebundenen Haltepunkte, die er bindet.  
  
  Prozess  
  Ein physischer Win32-Prozess. Ein Prozess kann mehrere Programme enthalten. Siehe auch *Programm*.  
  
  Programm  
  Ein einzelner Namespace, der innerhalb einer bestimmten Lauf Zeit Architektur ausgeführt wird. Siehe auch *Process*.  
  
  Sitzungs-Debug-Manager (SDM)  
  Verwaltet eine beliebige Anzahl von Debug-engines, die eine beliebige Anzahl von Programmen in mehreren Prozessen auf einer beliebigen Anzahl von Computern Debuggen. Auf der Basisebene ist SDM ein Multiplexer von Debug-engines. Außerdem bietet die SDM eine einheitliche Ansicht der Debugsitzung für die IDE.  
  
  Stapelrahmen  
  Stellt den Status der Berechnung für einen bestimmten Frame und eine bestimmte Ebene von aufrufenden aufrufenden-Funktionen dar.  
  
  thread  
  Das generalisierte Konzept der Stapel basierten Anweisungs Ausführung, das in mindestens einem Programm ausgeführt wird.  
  
  Warnungs-Haltepunkt  
  Eine Abstraktion zum Beschreiben einer Warnung in einem ausstehenden Breakpoint. Ein Warnungs Haltepunkt beschreibt einen Grund, warum der ausstehende Breakpoint noch nicht an einen Code Speicherort gebunden ist. Dies kann daran liegen, dass der Code für den vom ausstehenden Breakpoint beschriebenen Speicherort noch nicht geladen wurde, oder aus einem anderen Grund.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
