---
title: Erstellen von SharePoint-Funktionen | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9fa42efc654bd3835a4f1ec1a5002136813550a0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="creating-sharepoint-features"></a>Erstellen von SharePoint-Funktionen
  Sie können eine SharePoint-Funktion verwenden, um Gruppen von verwandten SharePoint-Projektelemente zur einfacheren Bereitstellung. Sie können Funktionen erstellen, Bereiche festlegen und andere Funktionen wie Abhängigkeiten zu markieren, mit der SharePoint-Funktions-Designer. Der Designer generiert auch ein Manifest, also eine XML-Datei, die einzelnen Funktionen beschreibt.  
  
## <a name="adding-features-to-the-sharepoint-solution"></a>Hinzufügen von Funktionen zu der SharePoint-Lösung  
 Sie können die SharePoint-Lösung mithilfe des Projektmappen-Explorer oder dem Paket-Explorer eine Funktion hinzuzufügen. Sie können eine der folgenden Methoden verwenden, eine Funktion hinzu.  
  
-   In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Funktionen**, und wählen Sie dann **Funktion hinzufügen**.  
  
-   In **Paket-Explorer**, öffnen Sie das Kontextmenü für das Paket, und wählen Sie dann **Funktion hinzufügen**.  
  
## <a name="using-the-feature-designer"></a>Mithilfe der Funktions-Designer  
 Eine SharePoint-Lösung kann eine oder mehrere SharePoint-Funktionen, enthalten, die unter dem Knoten "Funktion" im Projektmappen-Explorer gruppiert werden. Jede Funktion verfügt über eine eigene **Funktions-Designer** , dass Sie verwenden können, um die Funktionseigenschaften anzupassen. Weitere Informationen finden Sie unter [wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md). Um Funktionen voneinander zu unterscheiden, können Sie die Eigenschaften wie z. B. Titel, Beschreibung, Version und Bereich konfigurieren.  
  
### <a name="feature-designer-options"></a>Feature-Designeroptionen  
 Nach dem Erstellen einer Funktion können Sie die Funktions-Designer, um ihn anzupassen.  
  
 Die folgende Tabelle beschreibt die Eigenschaften, die in der Funktions-Designer angezeigt werden.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Titel|Dies ist optional. Der Standardtitel der Funktion festgelegt ist, um *SolutionName**FeatureName*.|  
|Beschreibung|Dies ist optional. Die Beschreibung der SharePoint-Funktion.|  
|Bereich|Erforderlich. Wenn eine Funktion erstellt wird **Projektmappen-Explorer**, der Bereich ist standardmäßig auf Web festgelegt.<br /><br /> -Farm: Aktivieren Sie eine Funktion für eine gesamte Serverfarm.<br /><br /> -Website: Aktivieren Sie eine Funktion für alle Websites in einer Websitesammlung.<br /><br /> -Website: Aktivieren Sie eine Funktion für eine bestimmte Website.<br /><br /> -WebApplication: Aktivieren Sie eine Funktion für alle Websites in einer Webanwendung.|  
|Elemente in der Lösung|Alle SharePoint-Elemente, die die Funktion hinzugefügt werden kann.|  
|Elemente in der Funktion|Die SharePoint-Projektelemente, die auf die Funktion hinzugefügt wurden.|  
  
## <a name="adding-and-removing-sharepoint-project-items"></a>Hinzufügen und Entfernen von SharePoint-Projektelemente  
 Sie können die SharePoint-Projektelemente auswählen, dass Sie eine SharePoint-Funktion zur Bereitstellung hinzufügen möchten. Verwenden der **Funktions-Designer** hinzufügen und Entfernen von Elementen in Funktionen und das Funktionsmanifest anzeigen. Weitere Informationen finden Sie unter [wie: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="adding-feature-dependencies"></a>Hinzufügen von Funktionsabhängigkeiten  
 Sie können das Funktionsmanifest konfigurieren, sodass die SharePoint-Server bestimmte Funktionen aktiviert, bevor die Funktion aktiviert ist. Z. B. wenn die SharePoint-Funktion auf andere Funktionen für Funktionen oder Daten abhängig ist, kann die SharePoint-Server zuerst versuchen, keines der Features zu aktivieren, die von die Funktion abhängig ist. Weitere Informationen finden Sie unter [wie: Hinzufügen und Entfernen von Funktionsabhängigkeiten](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Vorgehensweise: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Vorgehensweise: Hinzufügen und Entfernen von Funktionsabhängigkeiten](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  