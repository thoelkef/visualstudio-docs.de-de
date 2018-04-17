---
title: Feedback an den Benutzer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 629d12974a52bca30c0db96e838c5c731ae1abf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="feedback-to-the-user"></a>Feedback an den Benutzer
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) visuelles Feedback hinsichtlich verfügbare Funktionalität auf der aktuellen Auswahl und globalen Auswahlkontext des Benutzers basiert. In der folgenden Tabelle sind die Funktionen aufgeführt, die in verschiedenen Auswahl Kontexten verfügbar ist.  
  
|Auswahlkontext|Verfügbare Funktionen|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Aktuelle Produktgruppe|Produktspezifisch|  
|Aktive Hierarchie|Hierarchie-Typ-spezifisch|  
|Aktive Hierarchieelement|Hierarchie-Element-Typ-spezifisch|  
|Aktives Dokument|Dokument-Typ-spezifisch|  
|Fenster der obersten Multiple Document Interface (MDI)|Fenster Typ-spezifisch|  
|Aktuellen Auswahlkontext|Bestimmte Auswahlkontext|  
  
 Wenn Sie die Funktionalität nur Benutzer benötigen, und geben Sie ständig konsistent Auswahl und Umgebung Kontext Feedback anzuzeigen, verringern Sie die Komplexität in der IDE an. Die folgenden Regeln gelten immer, wenn ein Fenster in der IDE geöffnet wird:  
  
-   Wenn das Fenster seines Kontexts Auswahl ändert, Auswahl Feedback eindeutig angegeben wird, klicken Sie im Fenster und dynamischen Hilfefenster angezeigt, wenn angezeigt wird, wird den aktuellen Kontext entsprechend aktualisiert.  
  
-   Wenn das Fenster globale Auswahlkontext geändert wird, werden alle kontextspezifisch Menüs, die aktive Hierarchiefenster und Titelleiste der Anwendung entsprechend den aktuellen Kontext aktualisiert.  
  
-   Das Fenster Eigenschaften für die aktuelle Auswahl in surface sollte die **Eigenschaften** Fenster und (optional) angezeigt, die **Eigenschaftenseiten** (Dialogfeld).  
  
-   Wenn das Fenster nicht Eigenschaften Oberfläche oder globale Auswahlkontext ändern, sollten Auswahl Feedback nicht im Fenster bleiben, wenn er nicht mehr das aktive Fenster in der IDE ist.  
  
-   Das aktive Dokument sollten alle dokumentspezifische Toolfenster ständig berücksichtigt werden.  
  
-   Menüs, Symbolleisten und die Titelleiste für die Anwendung sollte das Clientfenster oberste Multiple Document Interface (MDI) entsprechen.  
  
 Z. B. wenn HTML-Ansicht des ein Web Form in einem Visual Basic-Webanwendungsprojekt wird geöffnet und der Benutzer wählt ein `<td>` Tag, Feedback bereitgestellt wie folgt:  
  
-   Auswahl im aktiven Fenster angegeben ist, und wirkt sich die **Eigenschaften** Fenster.  
  
-   Der Dokument-spezifische **Toolbox** wird das aktive Dokument entsprechend aktualisiert.  
  
-   Die **Editor** Symbolleiste und **Tabelle** Menü angezeigt werden und die Titelleiste der Web Form-Fenster entsprechend aktualisiert.  
  
-   Die aktive Hierarchiefenster, i. d. r. **Projektmappen-Explorer**, und das Title-Leiste Update entsprechend den aktuellen Kontext und dem kontextabhängigen **Projekt** Menübefehle jetzt zum aktiven Web anwenden -Anwendungsprojekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswahl und Währung, in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md)   
 [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)