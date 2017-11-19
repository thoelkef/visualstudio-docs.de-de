---
title: "Vorgehensweise: hinzufügen eine Ressourcendatei | Microsoft Docs"
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
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7233bc1a739bd3bf6544aad879f898bf3848ee7b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-resource-file"></a>Gewusst wie: Hinzufügen einer Ressourcendatei
  Die Befehle zum Hinzufügen von Ressourcendateien ist der Knoten "Projektmappe" und Feature-Knoten im Projektmappen-Explorer im Kontextmenü. Weitere Informationen finden Sie unter [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Eine SharePoint-Lösung eine globale Ressourcendatei hinzu  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], öffnen Sie eine SharePoint-Lösung.  
  
2.  In **Projektmappen-Explorer**, wählen Sie einen SharePoint-Projektknoten, und wählen Sie dann auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** Dialogfeld Wählen Sie die **globale Ressourcendatei** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
    > [!NOTE]  
    >  Die globale Ressourcendatei Projektelementvorlage nur angezeigt, wenn ein SharePoint-Projektelement ausgewählt ist.  
  
4.  In der **Ressource hinzufügen** Dialogfeld Wählen Sie eine Kultur der Ressourcendatei, z. B. Englisch (Vereinigte Staaten).  
  
     Dieser Schritt fügt eine globale Ressourcendatei der Projektmappe im Format Ressource*x***.** *Kultur***.** RESX, z. B. Resource1.en-US.resx.  
  
5.  Wenn die **Ressourcen-Editor** öffnet im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Hinzufügen von Ressourcen in der Ressourcendatei.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Hinzufügen eine Funktionsressourcendatei zu einer SharePoint-Funktion  
  
1.  Wenn die SharePoint-Lösung nicht bereits geöffnet ist, im ist [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], öffnen Sie die Projektmappe.  
  
2.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Namen einer Funktion unter den **Funktionen** Knoten, und wählen Sie dann **Funktionsressource hinzufügen**.  
  
     Dieser Schritt fügt eine Ressourcendatei mit der Funktion in das Format *ResourceFileName***.** *Kultur***.** RESX, z. B. Feature1.en-US.resx.  
  
3.  Wenn die **Ressourcen-Editor** öffnet im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Hinzufügen von Ressourcen in der Ressourcendatei.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  