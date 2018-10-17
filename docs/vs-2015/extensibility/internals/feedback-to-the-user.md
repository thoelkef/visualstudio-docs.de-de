---
title: Feedback an den Benutzer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0eb2942d0449e69ef25e26e6194d67bc7b0484e0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263839"
---
# <a name="feedback-to-the-user"></a>Feedback an den Benutzer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE), visuelles Feedback in Bezug auf verfügbare Funktionalität auf der aktuellen Auswahl und globale Auswahlkontext des Benutzers basiert. Die folgende Tabelle enthält die Funktionalität, die in andere Auswahl Kontexten verfügbar ist.  
  
|Auswahlkontext|Verfügbaren Funktionen|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Aktuelle Produktgruppe|Produktspezifisch|  
|Aktive Hierarchie|Hierarchie Typ spezifische|  
|Aktive Hierarchie-Element|Hierarchie Element Typ spezifische|  
|Aktive Dokument|Dokument Typ spezifische|  
|Fenster der obersten Multiple Document Interface (MDI)|Fenster Typ spezifische|  
|Aktuellen Auswahlkontext|Bestimmte Auswahlkontext|  
  
 Wenn Sie die Funktionalität nur Benutzer benötigen und kontinuierlich bereitstellen, konsistente Auswahl und Umgebung Kontext Feedback anzuzeigen, verringern Sie die Komplexität in der IDE. Die folgenden Regeln gelten immer, wenn ein Fenster in der IDE geöffnet wird:  
  
-   Wenn das Fenster seinen Auswahlkontext geändert wird, Auswahlfeedback eindeutig angegeben wird, klicken Sie im Fenster, und im Fenster Dynamische Hilfe angezeigt wird, wird den aktuellen Kontext entsprechend aktualisiert.  
  
-   Wenn das Fenster globale Auswahlkontext geändert wird, werden alle kontextspezifische Menüs, die aktive Hierarchie-Fenster und die Titelleiste der Anwendung entsprechend den aktuellen Kontext aktualisiert.  
  
-   Im Fenster sollten die Eigenschaften für die aktuelle Auswahl in Oberfläche der **Eigenschaften** Fenster und optional angezeigt, die **Eigenschaftenseiten** Dialogfeld.  
  
-   Wenn das Fenster nicht Eigenschaften Oberfläche oder globale Auswahlkontext ändern, sollten Auswahlfeedback nicht im Fenster bleiben, wenn er nicht mehr das aktive Fenster in der IDE ist.  
  
-   Alle für die spezifischen Toolfenster sollten kontinuierlich das aktive Dokument widerspiegeln.  
  
-   Menüs, Symbolleisten und die Titelleiste der Anwendung sollte das oberste Multiple Document Interface (MDI)-Clientfenster widerspiegeln.  
  
 Beispielsweise auf, wenn die HTML-Ansicht von einem Web Form innerhalb eines Projekts von Visual Basic-Webanwendung wird geöffnet und der Benutzer wählt eine `<td>` Tag, Feedback auf folgende Weise bereitgestellt:  
  
-   Auswahl in das aktive Fenster angegeben ist, und entsprechend in der **Eigenschaften** Fenster.  
  
-   Die Dokument-spezifischen **Toolbox** wird das aktive Dokument entsprechend aktualisiert.  
  
-   Die **Editor** Symbolleiste und **Tabelle** Menü angezeigt werden und der Titelleiste auf das Web Form-Fenster entsprechend aktualisiert.  
  
-   Die aktive Hierarchie-Fenster, in der Regel **Projektmappen-Explorer**, und das Title-Leiste Update entsprechend den aktuellen Kontext und dem kontextabhängigen **Projekt** Menübefehle jetzt anwenden, auf dem aktiven Web -Anwendungsprojekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)   
 [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)

