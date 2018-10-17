---
title: Bearbeiten und Fortfahren (Visual Basic) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61ce8f61092bdcc612ea535debfcface976ebff8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265102"
---
# <a name="edit-and-continue-visual-basic"></a>Bearbeiten und Fortfahren (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bearbeiten und Fortfahren ist eine Funktion von [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Debuggen, mit dem Sie den Code ändern können, während der Unterbrechungsmodus ausgeführt wird. Nachdem Codebearbeitungen übernommen wurden, können Sie die Ausführung mit den neuen Änderungen fortsetzen und deren Auswirkung beobachten.  
  
 Sie können die Funktion Bearbeiten und Fortfahren immer dann verwenden, wenn Sie sich im Unterbrechungsmodus befinden. Im Unterbrechungsmodus zeigt der Anweisungszeiger (eine gelbe Pfeilspitze im Quellcodefenster) auf die Zeile, die als nächste Zeile ausgeführt wird. Er wird auf eine ausführbare Anweisung innerhalb eines Methodentexts oder eines Eigenschaftentexts positioniert. Im Unterbrechungsmodus kann an einer ausführbaren Anweisung nahezu jede Änderung vorgenommen werden. Die vorgenommene Änderung wird im zugrunde liegenden Projekt übernommen. Allerdings ist es im Unterbrechungsmodus im Allgemeinen nicht zulässig, Deklarationsanweisungen, wie öffentliche Methoden, öffentliche Felder oder Klassendeklarationen, zu ändern.  
  
 Wenn Sie eine unberechtigte Bearbeitung vornehmen, wird die Änderung durch eine violette wellenförmige Linie gekennzeichnet, und in der Aufgabenliste wird eine Aufgabe angezeigt. Sie müssen eine unberechtigte Bearbeitung rückgängig machen, wenn Sie Bearbeiten und Fortfahren weiterhin verwenden möchten. Bestimmte unberechtigte Bearbeitungen sind möglicherweise zulässig, wenn sie außerhalb von Bearbeiten und Fortfahren durchgeführt werden. Wenn Sie die Ergebnisse einer solchen unberechtigten Bearbeitung beibehalten möchten, müssen Sie das Debuggen beenden und die Anwendung neu starten.  
  
 Die Funktion "Bearbeiten und Fortfahren" wird für 64-Bit-Projekte unterstützt, die auf .NET Framework 4.5.1 abzielen.  
  
 Bearbeiten und Fortfahren wird nicht unterstützt, beim Starten des Debuggens mit **an den Prozess anhängen**. Die Funktion „Bearbeiten und Fortfahren“ wird für Projekte mit optimiertem Code, Projekte mit gemischtem verwalteten und nativen Code sowie für Compact Framework-Projekte (intelligente Geräte) nicht unterstützt.  
  
 In den Themen zu diesem Abschnitt finden Sie weitere Informationen darüber, wie diese Funktion verwendet wird, und welche Arten von Änderungen nicht zulässig sind.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Gewusst wie: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von "Bearbeiten und Fortfahren"](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Erläutert, wie Codebearbeitungen im Unterbrechungsmodus vorgenommen werden.  
  
 [Nicht unterstützte Bearbeitungen beim Bearbeiten und Fortsetzen in Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Hier wird beschrieben, welche Arten von Bearbeitungen nicht mit der Funktion "Bearbeiten und Fortfahren" in [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] ausgeführt werden können.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)  
 Enthält eine Liste mit Themen zu Bearbeiten und Fortfahren.



