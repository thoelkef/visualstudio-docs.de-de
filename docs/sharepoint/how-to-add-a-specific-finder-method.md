---
title: "Vorgehensweise: hinzufügen eine bestimmten Finder-Methode | Microsoft Docs"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7b2277d725259fb5f95c186825773b5460ec17d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-specific-finder-method"></a>Gewusst wie: Hinzufügen einer bestimmten Finder-Methode
  Sie können eine einzelne Entitätsinstanz zurückgeben, durch das Erstellen einer *spezifischer Finder* Methode. Business Data Connectivity (BDC)-Dienst führt die spezifischer Finder-Methode auf, wenn ein Benutzer eine Entität in einem Business Data-Webpart oder eine externe Liste auswählt. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-specific-finder-method"></a>Erstellen eine bestimmten Finder-Methode  
  
1.  Wählen Sie eine Entität, auf dem BDC-Designer.  
  
     Informationen zur Vorgehensweise beim Hinzufügen einer Entität in den BDC-Designer in Visual Studio finden Sie unter [wie: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **BDC-Methodendetails**.  
  
     Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen zu diesem Fenster finden Sie unter [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der **Hinzufügen einer Methode** wählen **bestimmten Finder-Methode erstellen**.  
  
     Visual Studio fügt die folgenden Elemente für das Modell. Diese Elemente werden der **BDC-Methodendetails** Fenster.  
  
    -   eine Methode  
  
    -   Ein Eingabeparameter für die Methode.  
  
    -   Ein Rückgabeparameter für die Methode.  
  
    -   Ein Typdeskriptor für jeden Parameter.  
  
    -   Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Öffnen Sie Visual Studio **Eigenschaften** Fenster.  
  
5.  Konfigurieren Sie den Typdeskriptor des Rückgabeparameters als Entitätstypdeskriptor. Informationen über das Erstellen von Entitätstypdeskriptor finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Sie müssen diesen Schritt ausführen, wenn Sie die Entität eine Finder-Methode hinzugefügt haben. Visual Studio verwendet den Typdeskriptor, den Sie in der Finder-Methode definiert.  
  
    > [!NOTE]  
    >  Wenn die Bezeichnerfeld des Entitätstyps ein Feld in einer Datenbanktabelle, die automatisch generiert wird darstellt, legen Sie die **schreibgeschützte** Eigenschaft des Bezeichnerfelds ", **" true "**.  
  
6.  In der **Methodendetails** Fenster, wählen Sie die Methodeninstanz der Methode.  
  
7.  In der **Fenster "Eigenschaften"**legen die **Parametername zurückgeben** -Eigenschaft auf den Namen des Parameters der Methode zurück. Weitere Informationen zur Methode-Instanzeigenschaften finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü der Dienstcodedatei, die generiert wurde für die Entität, und wählen Sie dann **Code anzeigen**.  
  
     Die Entität Service-Codedatei wird im Code-Editor geöffnet. Weitere Informationen zu der Entität Service-Codedatei, finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Fügen Sie Code, der bestimmten Finder-Methode. Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Ruft einen Datensatz aus einer Datenquelle ab.  
  
    -   Gibt eine Entität mit dem BDC-Dienst.  
  
     Im folgende Beispiel wird ein Kontakt aus der AdventureWorks-Beispieldatenbank für SQL Server zurückgegeben.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert, der die `ServerName` Feld mit dem Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Vorgehensweise: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vorgehensweise: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Vorgehensweise: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  