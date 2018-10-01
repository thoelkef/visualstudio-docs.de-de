---
title: Das Dialogfeld für die Steuerelementbindung anpassen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datauicustomization
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Customize Control Binding dialog box
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4d47fe3962651db91dcfdf6e59653db539a9f44b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514594"
---
# <a name="customize-control-binding-dialog-box"></a>Dialogfeld „Steuerelementbindung anpassen“
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden der **Steuerelementbindung anpassen** angeben, welche Steuerelemente für Elemente im Dialogfeld die [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Jedes Element in der **Datenquellen** Fenster ist eine Liste von Steuerelementen, die auf das Element gebunden werden kann, die zugeordnet. Die Steuerelemente zur Verfügung, für die einzelnen Elemente werden durch den Datentyp des Elements bestimmt. Jeder Datentyp verfügt über eine Liste der gültigen zugeordneten Steuerelemente, die in diesem Dialogfeld an, einschließlich eines Standardsteuerelements definiert.  
  
 Bevor Sie ein Element auf eine Entwurfsoberfläche zum Erstellen eines datengebundenen Steuerelements ziehen, können Sie das Steuerelement zum Erstellen auswählen. Wenn Sie ein Element aus ziehen die **Datenquellen** Fenster auf einer Entwurfsoberfläche ohne ein Steuerelement, das standardmäßige Steuerelement auszuwählen, für der Datentyp des ausgewählten Elements auf der Entwurfsoberfläche hinzugefügt wird.  
  
 Weitere Informationen zur Verwendung dieses Dialogfeld können Sie zum Anpassen der Liste der Steuerelemente für Elemente in der **Datenquellen** Fenster finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Datentyp**  
 Zeigt eine Liste von Typen, die Sie mit Steuerelementen zuordnen:  
  
-   Tabellen, Entitäten und Objekte werden als dargestellt **[List]** Typen.  
  
-   Spalten oder öffentlichen Eigenschaften der Entitäten und Objekte werden als der eigentliche Datentyp der Spalte oder Eigenschaft in den zugrunde liegenden Datenspeicher dargestellt.  
  
-   Objekte mit benutzerdefinierten Formen werden als dargestellt **[andere]**. Wählen Sie beispielsweise, wenn Ihre Anwendung ein benutzerdefiniertes Steuerelement, in dem Daten aus mehr als eine Eigenschaft eines Objekts angezeigt verfügt, die **[andere]** -Datentyp für das Steuerelement.  
  
 **Zugeordneten Steuerelemente**  
 Zeigt eine Liste von Steuerelementen, die einen bestimmten Datentyp zugeordnet werden können. Wenn Sie ein bestimmtes Steuerelement mit dem Datentyp, der im ausgewählten zuordnen möchten die **Datentyp** wählen Sie das entsprechende Kontrollkästchen. Deaktivieren Sie dieses Kontrollkästchen, damit eine Zuordnung zu entfernen. Aktivierte Steuerelemente werden im Kontextmenü angezeigt, durch die **Datenquellen** Fenster für ein Element des Typs der zugeordneten Daten.  
  
 Sie können Steuerelemente zur Liste hinzufügen, durch Hinzufügen von Steuerelementen, die einen von mehreren Datenbindung-Attributen, enthalten die **Toolbox**. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Standard festlegen**  
 Weist der ausgewählte Steuerelementtyp der Standardwert für Elemente des ausgewählten Datentyps sein. Das standardmäßige Steuerelement angezeigt wird, als die erste Option im Kontextmenü angezeigt, durch die **Datenquellen** Fenster für ein Element. Als Standard für einen Datentyp kann nur ein Steuerelement-Typ zugewiesen werden.  
  
 **Standard löschen**  
 Entfernt die Bezeichnung eines Steuerelements als Standard für den ausgewählten Datentyp. Wenn es keinen Standardwert für den ausgewählten Datentyp gibt **[keine]** wird als erste Auswahl im Kontextmenü angezeigt, die von der **Datenquellen** Fenster für ein Element des zugeordneten Typs.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellenfenster](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Fügen Sie benutzerdefinierter Steuerelemente zum Datenquellenfenster hinzu](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)