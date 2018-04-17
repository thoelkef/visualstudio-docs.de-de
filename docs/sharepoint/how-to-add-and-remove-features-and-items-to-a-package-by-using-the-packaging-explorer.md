---
title: 'Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Explorer | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dafa11c17968eb5468ecd4eff462ff9474ce5131
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Gewusst wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Explorer
  Um ein Paket zum Bereitstellen von SharePoint-Projektelemente und-Funktionen zu konfigurieren, können Sie dem Paket-Explorer verwenden. Sie können die SharePoint-Projektelemente und-Funktionen in der WSP-Datei anpassen.  
  
 Alternativ können Sie die Paket-Designer verwenden, anzeigen und sortieren Sie die Funktionen, die die Aktivierungsreihenfolge zu ändern. Weitere Informationen finden Sie unter [wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="opening-the-packaging-explorer"></a>Öffnen die Paket-Explorer  
 Visual Studio-Projektmappe verfügt über mindestens ein SharePoint-Projekt, können Sie das folgende Verfahren verwenden, um zu dem Paket-Explorer zu öffnen. Alternativ wird die Paket-Explorer automatisch geöffnet, wenn Sie einen Feature oder Paket-Designer anzeigen. Nachdem Sie alle Funktion und Paket-Designer schließen, wird die Paket-Explorer ebenfalls geschlossen.  
  
#### <a name="to-open-the-packaging-explorer"></a>Um dem Paket-Explorer zu öffnen.  
  
1.  Wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **Paket-Explorer**.  
  
     Die **Paket-Explorer** wird angezeigt, der **Toolbox**.  
  
## <a name="adding-a-feature-to-a-package"></a>Hinzufügen einer Funktion zu einem Paket  
 Sie können neue und vorhandene Funktionen zu einem Paket hinzufügen, indem Sie mit der Paket-Explorer.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Hinzufügen einer SharePoint-Funktion  
  
1.  Öffnen Sie die **Paket-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Funktion hinzufügen**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>So verschieben Sie eine vorhandene SharePoint-Funktion  
  
1.  Öffnen der **Paket-Explorer**, und führen Sie einen der folgenden Schritte aus:  
  
    -   Ziehen Sie eine **Feature** von einem Projekt auf ein anderes Projekt.  
  
    -   Öffnen Sie das Kontextmenü für eine Funktion, wählen Sie **Ausschneiden**, öffnen Sie das Kontextmenü für das Projekt zu dem Sie die Funktion zu verschieben, und wählen Sie dann **einfügen**.  
  
    > [!NOTE]  
    >  Gehen Sie folgendermaßen vor, wenn Sie mehr als ein SharePoint-Projekt in der Projektmappe vorhanden.  
  
## <a name="validating-a-feature-or-package"></a>Überprüfen einer Funktion oder eines Pakets  
 Sie können ermitteln potenzieller Probleme in der SharePoint-Funktionen und Pakete überprüfen die Dateien. Warnungen und Fehler werden im Fenster "Ausgabe" und Fenster "Fehlerliste" angezeigt.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>So überprüfen Sie eine SharePoint-Funktion oder eines Pakets  
  
1.  Öffnen der **Paket-Explorer**.  
  
2.  Öffnen Sie ein Kontextmenü für eine Funktion oder ein Paket, und wählen Sie dann **Validate**.  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  