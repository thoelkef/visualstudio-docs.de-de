---
title: 'Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe den Paket-Explorer | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2dda4193a0ea30ac08f8a63a39ce00fb634832d7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596424"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe der Paket-Explorer
  Um ein Paket zum Bereitstellen von SharePoint-Elemente und Funktionen zu konfigurieren, können Sie die Paket-Explorer. Sie können die SharePoint-Projektelemente und-Funktionen in der WSP-Datei anpassen.

 Alternativ können Sie den Paket-Designer verwenden, um anzuzeigen, und die Funktionen, die die Aktivierungsreihenfolge ändern, neu anordnen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Öffnen Sie die Paket-Explorer
 Sie können das folgende Verfahren verwenden, um den Paket-Explorer zu öffnen verfügt Visual Studio-Projektmappe mindestens ein SharePoint-Projekt. Alternativ wird die Paket-Explorer automatisch geöffnet, wenn Sie einen Feature oder Paket-Designer anzeigen. Nachdem Sie alle Funktions- und Designer schließen, wird die Paket-Explorer ebenfalls geschlossen.

#### <a name="to-open-the-packaging-explorer"></a>Um den Paket-Explorer zu öffnen.

1.  Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **Paket-Explorer**.

     Die **Paket-Explorer** wird in der **Toolbox**.

## <a name="adding-a-feature-to-a-package"></a>Hinzufügen eines Features zu einem Paket
 Sie können neue und vorhandene Funktionen zu einem Paket mithilfe der Paket-Explorer hinzufügen.

#### <a name="to-add-a-sharepoint-feature"></a>Hinzufügen eine SharePoint-Funktion

1.  Öffnen Sie die **Paket-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Feature hinzufügen**.

#### <a name="to-move-an-existing-sharepoint-feature"></a>Verschieben einer vorhandenen SharePoint-Funktion

1.  Öffnen der **Paket-Explorer**, und führen Sie einen der folgenden Schritte aus:

    -   Ziehen Sie eine **Feature** aus einem Projekt auf ein anderes Projekt.

    -   Öffnen Sie das Kontextmenü für eine Funktion, und wählen **Ausschneiden**, öffnen Sie das Kontextmenü für das Projekt, das Sie verschieben Sie die Funktion, und wählen Sie dann möchten **einfügen**.

    > [!NOTE]
    >  Gehen Sie folgendermaßen vor, wenn Sie über mehr als eine SharePoint-Projekt in der Projektmappe verfügen.

## <a name="validate-a-feature-or-package"></a>Überprüfen Sie, ein Feature oder Paket
 Sie können potenzielle Probleme in der SharePoint-Funktionen und Pakete identifizieren, indem Sie die Dateien überprüfen. Warnungen und Fehler werden im Fenster "Ausgabe" und Fenster "Fehlerliste" angezeigt.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Um eine SharePoint-Funktion oder ein Paket zu überprüfen.

1.  Öffnen der **Paket-Explorer**.

2.  Öffnen Sie ein Kontextmenü für ein Feature oder Paket, und wählen Sie dann **überprüfen**.

## <a name="see-also"></a>Siehe auch
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
