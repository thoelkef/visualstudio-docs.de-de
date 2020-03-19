---
title: Fenster "Toolbox"
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7decdb80cd06b1af3230b2926c4ebd37b48e422
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596449"
---
# <a name="toolbox"></a>Toolbox

Im Fenster **Toolbox** werden Steuerelemente angezeigt, die Sie zu Visual Studio-Projekten hinzufügen können. Zum Öffnen der Toolbox klicken Sie im Menü **Ansicht** auf **Toolbox**.

![Fenster "Toolbox"](media/toolbox.png)

Sie können verschiedene Steuerelemente per Drag & Drop auf die Oberfläche des verwendeten Designers verschieben und die Größe und Position der Steuerelemente ändern.

Toolbox wird in Verbindung mit Entwurfsansichten angezeigt, wie der Designansicht einer XAML-Datei. In **Toolbox** werden nur die Steuerelemente angezeigt, die im aktuellen Designer verwendet werden können. Sie können eine Suche in **Toolbox** durchführen, um die Elemente zu filtern, die angezeigt werden.

> [!NOTE]
> Bei einigen Projekttypen werden in **Toolbox** möglicherweise keine Elemente angezeigt.

Die .NET-Version, auf die Ihr Projekt ausgerichtet ist, wirkt sich auch auf die Gruppe der Steuerelemente aus, die in Toolbox angezeigt wird. Sie können die Frameworkzielversion bei Bedarf über die Eigenschaftenseite des Projekts ändern. Wählen Sie den Projektknoten im **Projektmappen-Explorer** aus, und klicken Sie dann in der Menüleiste auf **Projekt** > **Projektname-Eigenschaften**. Verwenden Sie auf der Registerkarte **Anwendung** die Dropdownliste **Zielframework**.

## <a name="manage-the-toolbox-window-and-its-controls"></a>Verwalten des Toolbox-Fensters und dessen Steuerelemente

Standardmäßig wird **Toolbox** auf der linken Seite der Visual Studio-IDE reduziert dargestellt und wird angezeigt, wenn der Cursor darüber bewegt wird. Sie können **Toolbox** anheften (indem Sie auf das Symbol **Anheften** auf der Symbolleiste klicken), sodass diese geöffnet bleibt, wenn Sie den Cursor bewegen. Sie können das **Toolbox**-Fenster auch abdocken und es an eine beliebige Stelle auf dem Bildschirm ziehen. Sie können **Toolbox** andocken, abdocken und ausblenden, indem Sie mit der rechten Maustaste auf die Symbolleiste klicken und eine der Optionen auswählen.

Mithilfe der folgenden Befehle im Kontextmenü können Sie die Elemente auf einer **Toolbox**-Registerkarte neu anordnen oder benutzerdefinierte Registerkarten und Elemente hinzufügen:

- **Element umbenennen**: benennt das ausgewählte Element um.

- **Alle anzeigen**: zeigt alle möglichen Steuerelemente an (nicht nur die für den aktuellen Designer).

- **Listenansicht**: zeigt die Steuerelemente in einer vertikalen Liste an. Wenn dieses Kontrollkästchen deaktiviert ist, werden die Steuerelemente horizontal angezeigt.

- **Elemente auswählen**: öffnet das Dialogfeld **Toolboxelemente auswählen**, sodass Sie die Elemente festlegen können, die in der **Toolbox** angezeigt werden. Sie können ein Element ein- oder ausblenden, indem Sie dessen Kontrollkästchen aktivieren oder deaktivieren.

- **Elemente alphabetisch sortieren**: sortiert die Elemente nach Namen.

- **Toolbox zurücksetzen**: Stellt die Standardeinstellungen von **Toolbox** und die Standardelemente wieder her.

- **Registerkarte hinzufügen**: Fügt eine neue **Toolbox**-Registerkarte hinzu.

- **Nach oben**: verschiebt das ausgewählte Element nach oben.

- **Nach unten**: verschiebt das ausgewählte Element nach unten.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Erstellen und Verteilen von benutzerdefinierten Toolbox-Steuerelementen

Sie können benutzerdefinierte **Toolbox**-Steuerelemente erstellen und mit einer Projektvorlage beginnen, die auf [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) oder [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md) basiert. Sie können Ihr benutzerdefiniertes Steuerelement dann an Ihre Teamkollegen verteilen oder es im Internet mithilfe des [Installationsprogramms für Toolboxsteuerelemente](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx) veröffentlichen.

## <a name="help-on-toolbox-tabs"></a>Hilfe zu Toolboxregisterkarten

In den folgenden Themen werden weitere Informationen zu den verschiedenen **Toolbox**-Registerkarten bereitgestellt:

- [Toolbox, Registerkarte „Daten“](../../ide/reference/toolbox-data-tab.md)
- [Toolbox, Registerkarte „Komponenten“](../../ide/reference/toolbox-components-tab.md)
- [Toolbox, Registerkarte „HTML“](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Weitere Informationen

- [Toolboxelemente auswählen, WPF-Komponenten](choose-toolbox-items-wpf-components.md)
