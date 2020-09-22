---
title: 'Vorgehensweise: Beschränken der Instrumentierung auf bestimmte Funktionen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8923323a3aed96a9dd441a4a36b2084ffd8197e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840901"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Gewusst wie: Beschränken der Instrumentation auf bestimmte Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Instrumentierung und Datensammlung auf eine oder mehr Funktionen einschränken, indem Sie die Optionen unter der Seite **Erweitert** der **Leistungssitzung** oder die Zielbinärdateieigenschaften einstellen.  
  
- Wenn Sie die Funktionen auf der Eigenschaftenseite der Leistungssitzung angeben, werden nur diese Funktionen in allen instrumentierten Binärdateien der Sitzung instrumentiert.  
  
- Wenn Sie die Funktionen auf der Eigenschaftenseite einer Zielbinärdatei angeben, werden nur die Funktionen, die in dieser bestimmten Binärdatei sind, instrumentiert. Funktionen in anderen Leistungsbinärdateien werden wie gewohnt instrumentiert.  
  
  Das beschränken der Datensammlung auf diese Weise wird nur unterstützt, wenn die Instrumentierungs-Profilerstellungsmethode ausgewählt ist.  
  
> [!NOTE]
> Sie können auch die Seite **Erweitert** der Eigenschaftenseiten **Leistungssitzung** verwenden, um andere Einstellungen zu verwenden, die für das Befehlszeilen-Instrumentierungstool [VSInstr](../profiling/vsinstr.md) verfügbar sind.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>So beschränken Sie die Instrumentierung auf bestimmte Funktionen in einer Leistungssitzung  
  
1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf den Namen der Sitzung, und klicken Sie dann auf **Eigenschaften**.  
  
    Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.  
  
2. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **Erweitert**  
  
3. Verwenden Sie im Textfeld **Zusätzliche Instrumentierungsoptionen** den folgenden Syntax, um den Namen der zu instrumentierenten Funktionen einzugeben:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` ist der Namespace und der Funktionsname. Es hat das Format `Namespace` **::** `FunctionName`. Trennen Sie mehrere Funktionen mit einem Semikolon. Verwenden Sie ein Sternchen (\*), um einen Platzhalter für ein oder mehrere Zeichen anzugeben. Beispiel: **/include:MyNS::\\** * gibt alle Funktionen im Namespace „MyNS“ an.  
  
   > [!NOTE]
   > Öffnen Sie zum Auflisten der Funktionen in einer Binärdatei ein Eingabeaufforderungsfenster im Installationsverzeichnis des Profilerstellungstools (in der Regel das Verzeichnis \Team Tools\Performance Tools unter dem Installationsverzeichnis [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]), und geben Sie anschließend **vsinstr /DumpFuncs** ein.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>So beschränken Sie die Instrumentierung auf eine bestimmte Funktion in einer Binärdatei  
  
1. Suchen Sie im **Leistungs-Explorer** den Namen der Binärdatei im Knoten **Ziele** der Leistungssitzung.  
  
2. Klicken Sie mit der rechten Maustaste auf den Namen der Binärdatei, und klicken Sie anschließend auf **Eigenschaften**.  
  
    Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.  
  
3. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **Erweitert**  
  
4. Verwenden Sie im Textfeld **Zusätzliche Instrumentierungsoptionen** den folgenden Syntax, um den Namen der zu instrumentierenten Funktionen einzugeben:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` ist der Namespace und der Funktionsname. Es hat das Format `Namespace` **::** `FunctionName`. Trennen Sie mehrere Funktionen mit einem Semikolon. Verwenden Sie ein Sternchen (\*), um einen Platzhalter für ein oder mehrere Zeichen anzugeben. Beispiel: **/include:MyNS::\\** * gibt alle Funktionen im Namespace „MyNS“ an.  
  
   > [!NOTE]
   > Öffnen Sie zum Auflisten der Funktionen in einer Binärdatei ein Eingabeaufforderungsfenster im Installationsverzeichnis des Profilerstellungstools (in der Regel das Verzeichnis \Team Tools\Performance Tools unter dem Installationsverzeichnis [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]), und geben Sie anschließend **vsinstr /DumpFuncs** ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Gewusst wie: Beschränken der Instrumentierung auf bestimmte DLLs](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Gewusst wie: Angeben zusätzlicher Instrumentierungs Optionen](../profiling/how-to-specify-additional-instrumentation-options.md)
