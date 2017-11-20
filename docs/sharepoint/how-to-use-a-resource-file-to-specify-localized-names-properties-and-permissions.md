---
title: 'Vorgehensweise: Verwenden Sie eine Ressourcendatei angeben von lokalisierten Namen, Eigenschaften und Berechtigungen | Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a8b61477ae3b588b2aeadf1c9d99618151825f8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei
  Mithilfe einer Ressourcendatei können Sie lokalisierte Namen bereitstellen, definieren Sie Eigenschaften und wenden Berechtigungen Tor-Objekte, die in einem Business Data Connectivity (BDC)-Modell definiert sind. Um diese Informationen anzugeben, fügen Sie eine **Business Data Connectivity-Ressource** Element aus, um ein Projekt mit einem **Business Data Connectivity-Modell** Element. Dann geben Sie Namen, Eigenschaften und Berechtigungen durch Bearbeiten den XML-Code für die Ressourcendatei.  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Um ein BDC-Ressourcendatei einem SharePoint-Projekt hinzufügen  
  
1.  In **Projektmappen-Explorer**, erweitern Sie den Ordner für die SharePoint-Projekt, und wählen Sie dann den Ordner mit dem BDC-Modell.  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
3.  Erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  In der **neues Element hinzufügen** Dialogfeld Wählen Sie **Business Data Connectivity-Ressourcenelement**.  
  
5.  In der **Namen** Feld Geben Sie den Namen der Ressourcendatei, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Eine Ressourcendatei, die der Erweiterung .bdcr wird dem Projekt hinzugefügt und für die Bearbeitung geöffnet.  
  
6.  Fügen Sie XML-Code, zum Definieren der lokalisierten Namen, Eigenschaften und Berechtigungen, die Sie das BDC-Modell anwenden möchten.  
  
     Informationen zum Definieren dieser Elemente finden Sie unter [Modell und Ressourcendateien](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: hinzufügen eine vorhandene BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  