---
title: Erstellen von SharePoint-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 56bc4dbd50bedc15fcf6c69cbc334fe09c6094cc
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325598"
---
# <a name="create-sharepoint-features"></a>Erstellen von SharePoint-features
  Sie können eine SharePoint-Funktion verwenden, zum Gruppieren verwandter Elemente der SharePoint-Projekt zur einfacheren Bereitstellung. Sie können Funktionen erstellen, Bereiche festlegen und andere Funktionen als Abhängigkeiten zu markieren, mit dem SharePoint-Funktions-Designer. Der Designer generiert außerdem ein Manifest, eine XML-Datei handelt, die jede Funktion beschreibt.  
  
## <a name="add-features-to-the-sharepoint-solution"></a>Hinzufügen von Funktionen zu der SharePoint-Lösung
 Sie können eine Funktion mithilfe des Projektmappen-Explorer oder die Paket-Explorer mit der SharePoint-Lösung hinzufügen. Sie können eine der folgenden Methoden verwenden, um ein Feature hinzufügen.  
  
-   In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Features**, und wählen Sie dann **Feature hinzufügen**.  
  
-   In **Paket-Explorer**, öffnen Sie das Kontextmenü für das Paket aus, und wählen Sie dann **Feature hinzufügen**.  
  
## <a name="using-the-feature-designer"></a>Verwenden die Funktions-designer
 Eine SharePoint-Lösung kann eine oder mehrere SharePoint-Funktionen enthalten, die unter dem Knoten "Funktion" im Projektmappen-Explorer gruppiert werden. Jede Funktion verfügt über eine eigene **Funktions-Designer** , Sie verwenden können, um die Feature-Eigenschaften anpassen. Weitere Informationen finden Sie unter [wie: Anpassen eines SharePoint-Features](../sharepoint/how-to-customize-a-sharepoint-feature.md). Um Funktionen voneinander zu unterscheiden, können Sie die Feature-Eigenschaften, z. B. Titel, Beschreibung, Version und Bereich konfigurieren.  
  
### <a name="feature-designer-options"></a>Feature-Designeroptionen
 Nachdem Sie eine Funktion erstellt haben, können Sie die Funktions-Designer, anpassen.  
  
 Die folgende Tabelle beschreibt die Feature-Eigenschaften, die in der Funktions-Designer angezeigt werden.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Titel|Dies ist optional. Der Standardtitel des Features nastaven NA hodnotu *SolutionName* *FeatureName*.|  
|Beschreibung|Dies ist optional. Die Beschreibung der SharePoint-Funktion.|  
|Bereich|Erforderlich. Wenn eine Funktion erstellt wird, mithilfe von **Projektmappen-Explorer**, ist der Bereich standardmäßig Web festgelegt.<br /><br /> -Farm: Aktivieren Sie eine Funktion für eine gesamte Serverfarm.<br /><br /> -Site: Aktivieren Sie eine Funktion für alle Websites in einer Websitesammlung.<br /><br /> -Website: Aktivieren Sie eine Funktion für eine bestimmte Website.<br /><br /> -WebApplication: Aktivieren Sie eine Funktion für alle Websites in einer Webanwendung.|  
|Elemente in der Lösung|Alle SharePoint-Projektelemente, die die Funktion hinzugefügt werden können.|  
|Elemente in der Funktion|Die SharePoint-Projektelemente, die mit dem Feature hinzugefügt wurden.|  
  
## <a name="add-and-remove-sharepoint-project-items"></a>Hinzufügen und Entfernen von SharePoint-Projektelemente
 Sie können die SharePoint-Projektelemente auswählen, dass Sie eine SharePoint-Funktion, für die Bereitstellung hinzufügen möchten. Verwenden der **Funktions-Designer** hinzufügen und Entfernen von Elementen in Funktionen und das Funktionsmanifest anzuzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="add-feature-dependencies"></a>Hinzufügen von funktionsabhängigkeiten
 Sie können das Funktionsmanifest konfigurieren, damit, dass der SharePoint-Server eine bestimmte Funktionen aktiviert, bevor das Feature aktiviert ist. Z. B. Wenn Ihr SharePoint-Feature weitere Funktionen für Funktionen oder Daten abhängig ist, kann die SharePoint-Server zunächst versuchen, keines der Features zu aktivieren, die die Funktion abhängt. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von funktionsabhängigkeiten](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Siehe auch
 [Gewusst wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Gewusst wie: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Gewusst wie: Hinzufügen und Entfernen von funktionsabhängigkeiten](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  
