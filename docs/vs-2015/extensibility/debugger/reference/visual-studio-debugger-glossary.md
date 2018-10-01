---
title: Visual Studio-Debugger-Glossar | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da2b0d2c435cbfc0bca19977074a7b54e8de6315
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515149"
---
# <a name="visual-studio-debugger-glossary"></a>Glossar zum Visual Studio-Debugger
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Visual Studio-Debugger-Glossar](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/visual-studio-debugger-glossary).  
  
Im folgenden sind die Begriffe in der [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Debugging-SDK.  
  
## <a name="terms"></a>Begriffe  
 gebundene Haltepunkt  
 Eine Abstraktion für einen Haltepunkt im Code festgelegt werden soll. Es ist eine direkte Beziehung zwischen einen gebundenen Haltepunkt und eine Anweisung Haltepunkt im Code-Datenstrom. Wenn der code entladen, gebundener Haltepunkte möglicherweise Aufheben der Bindung.  
  
 Kausalität  
 Bietet die Möglichkeit, einen logischen Thread der Ausführung auf mehrere physische Threads, Prozesse und Computer nachzuverfolgen und um die Aufrufliste dieses logischen Threads zu einem bestimmten Zeitpunkt in der Lebensdauer des Threads zu rekonstruieren.  
  
 Codekontext  
 Stellt eine Abstraktion einer Position im Code bekannt, dass die Debug-Engine. Für die meisten Laufzeitfehler-Architekturen ist ein Codekontext eine Adresse im Anweisungsstream eines Programms. Für nicht traditionelle Sprachen, in denen Code Anweisungen nicht dargestellt werden kann, kann ein Codekontext mithilfe anderer Methoden dargestellt werden.  
  
 der Pfad  
 Stellt einen Punkt der Ausführung im Code, in denen eine Abzweigung verwendet wird oder die Funktion wird aufgerufen. Eine stapelüberwachung ist praktisch eine Liste von Funktion Aufruf Codepfade.  
  
 Debug-Engine (DE)  
 Eine Komponente, die ermöglicht das Debuggen von einer Runtime-Architektur. Eine Debug-Engine funktioniert in Verbindung mit dem Betriebssystem oder -Interpreter und Debuggen von Diensten wie z. B. Ausführung-Steuerelement, Haltepunkte und Ausdruck Auswertung enthält.  
  
 Dokumentkontext  
 Stellt eine Abstraktion einer Position in einer Datei-Quelldokument bekannt, dass die Debug-Engine. Für die meisten Sprachen ist ein Dokumentkontext eine Position in einer Quelldatei. Für nicht traditionelle Sprachen, für die die Quelldatei Text möglicherweise nicht möglicherweise ein Dokumentenkontext andere Weise dargestellt werden. Siehe auch *dokumentieren Position*.  
  
 Dokumentposition  
 Stellt eine Abstraktion einer Position in einer Quelldatei, die bekanntermaßen von der IDE. Für die meisten Sprachen wird eine Dokumentposition einer Position in einer Quelldatei. Für nicht traditionelle Sprachen wird möglicherweise eine Dokumentposition auf andere Weise dargestellt werden. Siehe auch *Dokumentkontext*.  
  
 Fehler-Haltepunkt  
 Eine Abstraktion für einen Fehler in ein ausstehender Haltepunkt beschreiben. Ein Haltepunkt auf Fehler unter Umständen einen Fehler in den Speicherort der ausstehenden Haltepunkt, den Ausdruck, der mit den ausstehenden Haltepunkt oder andere Informationen, die Bindung den ausstehenden Haltepunkt an einem codespeicherort verhindert beschreiben.  
  
 Auswertungskontext  
 Stellt eine Abstraktion der ein Programmierungskontext für die Auswertung von Ausdrücken bereit. In der Regel mit ein Evaluierungskontext ein Bereich ist. Bei der Auswertung des Ausdrucks in einem Ausdruckskontext bietet der Ausdruckskontext Bereichsregeln, die der Zeitpunkt der Erstellung zu entsprechen. Beispielsweise wird ein Ausdruckskontext erstellt, die in einem Stapelrahmen der Kontext bereitgestellt, für Ihre Evaluierung von lokalen Variablen, Methodenparameter, Klasse, Elemente (falls zutreffend) und globale Variablen.  
  
 abgefangene Ausnahme  
 Eine Ausnahme, die von einer Debug-Engine abgefangen wird, auch wenn kein Mechanismus zur Ausnahmebehandlung direkt in den aktuellen Stapelrahmen ist.  
  
 JustMyCode  
 Das Konzept der nur den Code Debuggen, der zu einem Benutzer gehört, und wird ignoriert, alle temporären Code wie z. B. Systemcode – selbst wenn der Quellcode für diesen Systemcode verfügbar ist.  
  
 ausstehender Haltepunkt  
 Stellt eine Abstraktion für Haltepunkte vor, während und nach dem Code ist geladen, und es wird eine Möglichkeit, Haltepunkte zu virtualisieren. Ein ausstehender Haltepunkt:  
  
-   Enthält alle Informationen, die erforderlich sind, einen Haltepunkt für Code in einem oder mehreren Programmen zu binden.  
  
-   Können eine Bindung an mehreren Standorten von Code in einem oder mehreren Programmen.  
  
-   Bindet niemals selbst Code.  
  
 Jedes Mal Code lädt, alle ausstehenden Haltepunkte in einem Programm werden überprüft, um festzustellen, ob sie binden können. Ein ausstehender Haltepunkt ist dann alle gebundenen Breakpoints enthalten, die gebunden wird.  
  
 process  
 Ein physischer Win32-Prozess. Ein Prozess kann mehrere Programme enthalten. Siehe auch *Programm*.  
  
 Programm  
 Ein einzelner Namespace, die in einer bestimmten Laufzeit-Architektur ausgeführt wird. Siehe auch *Prozess*.  
  
 sitzungsbasierter Debug-Manager (SDM)  
 Verwaltet eine beliebige Anzahl von Debug-Engines, die eine beliebige Anzahl von Programmen in mehreren Prozessen auf eine beliebige Anzahl von Computern zu debuggen. Auf der Basisebene ist das SDM ein multiplexer der Debug-Engines. Darüber hinaus bietet das SDM eine einheitliche Ansicht der Debugsitzung der IDE.  
  
 Stapelrahmen  
 Stellt den Status der Berechnung auf einem bestimmten Frame und Maß Aufrufe geschachtelter Funktionen dar.  
  
 Thread  
 Das generalisierte Konzept der Anweisung stapelbasierten Ausführung auf mindestens ein Programm.  
  
 Haltepunkt mit Warnung  
 Eine Abstraktion zum Beschreiben der in ein ausstehender Haltepunkt einer Warnung. Ein Haltepunkt für die Warnung beschreibt einen Grund, warum der ausstehenden Haltepunkt noch nicht an einen Speicherort gebunden wurde. Dies kann sein, dass der Code noch nicht für den Speicherort der ausstehenden Haltepunkt beschrieben oder einem anderen Grund geladen ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

