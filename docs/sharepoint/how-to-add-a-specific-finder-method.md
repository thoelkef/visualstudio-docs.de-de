---
title: 'Vorgehensweise: hinzufügen eine bestimmten Finder-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7319842d0c90b18b170fcd5e199dc255f45a3374
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758435"
---
# <a name="how-to-add-a-specific-finder-method"></a>Gewusst wie: hinzufügen eine bestimmte Finder-Methode
  Sie können eine einzelne Entitätsinstanz zurück, durch das Erstellen einer *spezifische Finder* Methode. Der Business Data Connectivity (BDC)-Dienst führt die spezifische Finder-Methode auf, wenn ein Benutzer eine Entität in einem Business Data-Webpart oder eine externe Liste auswählt. Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-specific-finder-method"></a>Zum Erstellen einer bestimmten Finder-Methode
  
1.  Auf der **BDC-Designer**, wählen Sie eine Entität.  
  
     Informationen zur Vorgehensweise beim Hinzufügen einer Entität für die **BDC-Designer** in Visual Studio finden Sie unter [Vorgehensweise: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows**, **BDC-Methodendetails**.  
  
     Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen zu diesem Fenster, finden Sie unter [BDC-Modell-Designtools Übersicht](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der **Hinzufügen einer Methode** wählen **spezifische Finder-Methode erstellen**.  
  
     Visual Studio fügt die folgenden Elemente für das Modell. Diese Elemente werden angezeigt, der **BDC-Methodendetails** Fenster.  
  
    -   eine Methode  
  
    -   Ein Eingabeparameter für die Methode.  
  
    -   Ein Rückgabeparameter für die Methode.  
  
    -   Ein Typdeskriptor für jeden Parameter.  
  
    -   Eine Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Öffnen Sie die Visual Studio **Eigenschaften** Fenster.  
  
5.  Konfigurieren Sie den Typdeskriptor des Parameters zurück, als Typ einen Deskriptor einer Entität. Informationen zum Typ einen Deskriptor einer Entität zu erstellen, finden Sie unter [wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Sie müssen diesen Schritt ausführen, wenn Sie die Entität eine Finder-Methode hinzugefügt haben. Visual Studio verwendet den Typdeskriptor, den Sie in der Finder-Methode definiert.  
  
    > [!NOTE]  
    >  Wenn das Feld "ID" des Entitätstyps ein Feld in einer Datenbanktabelle, der automatisch generiert wird darstellt, legen Sie die **schreibgeschützte** Eigenschaft des Bezeichnerfelds, **"true"**.  
  
6.  In der **Methodendetails** Fenster, wählen Sie die Methodeninstanz der Methode.  
  
7.  In der **Fenster "Eigenschaften"** legen die **Rückgabeparametername** -Eigenschaft auf den Namen des Parameters der Methode zurück. Weitere Informationen zu den Eigenschaften der Instanz, finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  In **Projektmappen-Explorer**, öffnen Sie im Kontextmenü des der Authentifizierungsdienst-Codedatei, die generiert wurde für die Entität aus, und wählen Sie dann **Ansichtscode**.  
  
     Die Entität Authentifizierungsdienst-Codedatei wird im Code-Editor geöffnet. Weitere Informationen zu der Entität Authentifizierungsdienst-Codedatei, finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Fügen Sie Code für die spezifische Finder-Methode. Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Ruft einen Datensatz aus einer Datenquelle ab.  
  
    -   Gibt eine Entität mit dem BDC-Dienst.  
  
     Im folgende Beispiel wird ein Kontakt aus der AdventureWorks-Beispieldatenbank für SQL Server zurückgegeben.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert der `ServerName` Feld mit dem Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>Siehe auch
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Gewusst wie: hinzufügen eine Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Gewusst wie: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
