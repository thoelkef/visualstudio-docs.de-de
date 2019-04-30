---
title: 'Vorgehensweise: Add-In-Benutzeroberflächenfehler anzeigen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 78cc4d2e85e2f7a5347fe0c8927c855160fbb511
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441793"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Vorgehensweise: Add-In-Benutzeroberflächenfehler anzeigen
  Wenn ein VSTO-Add-in versucht, die Microsoft Office-Benutzeroberfläche (UI) und ein Fehler auftritt, bearbeiten, wird standardmäßig keine Fehlermeldung angezeigt. Sie können Microsoft Office-Anwendungen aber so konfigurieren, dass Meldungen für Fehler angezeigt werden, die sich auf die Benutzeroberfläche beziehen. Sie können diese Nachrichten verwenden, um zu ermitteln, warum ein Menüband nicht angezeigt wird, oder warum ein Menüband angezeigt wird, jedoch keine Steuerelemente angezeigt werden.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>So zeigen Sie VSTO-Add-In-Benutzeroberflächenfehler an

1. Starten Sie die Anwendung.

2. Klicken Sie auf die Registerkarte **Datei** .

3. Klicken Sie auf **Optionen**.

4. Klicken Sie im Bereich "Kategorien" auf **Erweitert**.

5. Wählen Sie im Detailbereich die Option **VSTO-Add-In-Benutzeroberflächenfehler anzeigen**aus, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Für Outlook befindet sich das Kontrollkästchen **VSTO-Add-In-Benutzeroberflächenfehler anzeigen** im Abschnitt **Entwickler** des Detailbereichs. Für andere Anwendungen befindet sich das Kontrollkästchen im Abschnitt **Allgemein** des Detailbereichs.

## <a name="see-also"></a>Siehe auch
- [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)
- [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
