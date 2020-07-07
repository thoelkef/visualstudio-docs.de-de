---
title: 'Vorgehensweise: Einschließen einer benutzerdefinierten Assembly in eine BDC-Funktion | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 772cdbaca67cc82fc6b7eb2c5ef5adb6508df34a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015264"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Vorgehensweise: Einschließen einer benutzerdefinierten Assembly in eine BDC-Funktion
  Das Projekt kann auf Assemblys aus anderen Projekten in derselben Projekt Mappe verweisen. Allerdings müssen Sie diese Assemblys mithilfe des Dialog Felds referenzierte Assemblys **auf lobsystems zuweisen** der Featuredatei des Projekts hinzufügen.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>So fügen Sie eine benutzerdefinierte Assembly in ein Business Data Connectivity (BDC)-Feature ein

1. Wählen Sie in **Projektmappen-Explorer**den Ordner aus, der das BDC-Modell enthält.

2. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

3. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft Assemblys und **dann die Schalt** Fläche mit den Auslassungs Punkten aus (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")).

     Das Dialogfeld referenzierte Assemblys **zu lobsystems zuweisen** wird angezeigt.

4. Wählen Sie in der Liste **Wählen Sie eine Assembly** aus die benutzerdefinierte Assembly aus.

    > [!NOTE]
    > Assemblys werden nur im Dialogfeld **Zuweisen von referenzierten Assemblys zu lobsystems** angezeigt, wenn Sie einen Verweis auf das Projekt hinzugefügt haben, das die Assembly enthält. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen oder Entfernen von verweisen mithilfe des Dialog Felds "Verweis hinzufügen](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)".

5. Öffnen Sie in der Gruppe **Verweis Eigenschaften** die Liste, die für die Eigenschaft **LobSystem Scope** angezeigt wird, wählen Sie das Branchen System der Methoden aus, die die benutzerdefinierte Assembly verwenden, und klicken Sie dann auf die Schaltfläche **OK** .

    > [!NOTE]
    > Zum Debuggen von Code in der benutzerdefinierten Assembly müssen Sie die Assembly dem Projektmappenpaket hinzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und Entfernen zusätzlicher](../sharepoint/how-to-add-and-remove-additional-assemblies.md)Assemblys.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcen Datei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
