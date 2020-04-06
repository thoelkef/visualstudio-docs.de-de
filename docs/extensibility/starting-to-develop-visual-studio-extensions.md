---
title: Beginnen mit der Entwicklung von Visual Studio-Erweiterungen | Microsoft Docs
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699742"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Beginnen mit der Entwicklung von Visual Studio-Erweiterungen

Wenn Sie noch nie eine Visual Studio-Erweiterung geschrieben haben, haben Sie wahrscheinlich einige Fragen. Wir haben hier einige der häufigsten aufgelistet. Wenn die gesuchten Informationen nicht angezeigt werden, verwenden Sie die Feedback-Schaltflächen **(War diese Seite hilfreich?** am unteren Bildschirmrand), um nach dem zu fragen, was Sie wollen.

> [!NOTE]
> Dieser Artikel gilt für Visual Studio unter Windows. Weitere Informationen finden Sie unter [Erweitern von Visual Studio für Mac](/visualstudio/mac/extending-visual-studio-mac). Informationen zu Visual Studio-Code finden Sie unter [Visual Studio Code Extension API](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Welche Software benötige ich, um Visual Studio-Erweiterungen zu entwickeln?

Sie müssen das Visual Studio SDK zusätzlich zu Visual Studio installieren, um Visual Studio-Erweiterungen zu entwickeln. Sie können das Visual Studio SDK als Teil der regulären Einrichtung installieren oder später installieren. Weitere Informationen zum Installieren des Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Welche Arten von Dingen kann ich mit Visual Studio-Erweiterungen tun?

Der Himmel ist die Grenze, wenn es darum geht, sich verschiedene Visual Studio-Erweiterungen vorzustellen. Natürlich haben die meisten Erweiterungen etwas mit dem Schreiben von Code zu tun, aber das muss nicht der Fall sein. Hier sind einige Beispiele für die Arten von Erweiterungen, die Sie erstellen können:

- Unterstützung für Sprachen, die nicht in Visual Studio enthalten sind, mit Syntaxfärbung, IntelliSense sowie Compiler- und Debugunterstützung

- Produktivitätstools, die das IDE-Kernerlebnis mit zusätzlichen Vorlagen, Codeumgestaltung, neuen Dialogfeldern oder Toolfenstern erweitern

- Domänenspezifische Designer für Szenarien wie Datendesign oder Cloud-Support

Beispiele für Erweiterungen finden Sie im [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Viele Erweiterungen sind Open Source, und der Marketplace enthält Links zu ihrem GitHub-Repository.

## <a name="which-visual-studio-features-can-i-extend"></a>Welche Visual Studio-Funktionen kann ich erweitern?

Theoretisch können Sie fast jeden Teil von Visual Studio erweitern: Menüs, Symbolleisten, Befehle, Fenster, Lösungen, Projekte, Editoren usw.

In der Praxis haben wir festgestellt, dass die Funktionen, die die meisten Menschen erweitern möchten, Befehle, Menüs und Symbolleisten, Fenster, IntelliSense und Projekte sind. Hier sind Links zu den relevanten Abschnitten:

- [Erweitern von Menüs und Befehlen:](../extensibility/extending-menus-and-commands.md)Fügen Sie ihre eigenen Elemente zu Visual Studio-Menüs und Symbolleisten hinzu. Sie können sie verwenden, um neue Visual Studio-Funktionen oder eigene externe Hilfsanwendungen zu starten. Sie können auch benutzerdefinierte Verknüpfungen für Ihre Menüelemente bereitstellen.

- [Erweiterungs- und Customizing-Tool Windows:](../extensibility/extending-and-customizing-tool-windows.md)Erweitern Sie vorhandene Toolfenster oder erstellen Sie Ihre eigenen Toolfenster. Sie können z. B. neue Eigenschaften zu den **Eigenschaften**hinzufügen oder ein neues Toolfenster erstellen, um zusätzliche Features hinzuzufügen.

- [Editor- und Sprachdiensterweiterungen:](../extensibility/editor-and-language-service-extensions.md)Fügen Sie den für Visual Studio bereitgestellten IntelliSense-Sprachen eigene Anpassungen hinzu, oder erstellen Sie Unterstützung für neue Programmiersprachen. Sie können neue Anweisungsvervollständigungen, Vorschläge und neue QuickInfo-Tooltips erstellen. Mit Glühbirnen können Sie Umgestaltungsvorschläge und Codefixes hinzufügen, um neue Programmiersprachen zu unterstützen.

- [Erweitern von Projekten](../extensibility/extending-projects.md)

- [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)

- [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)

- [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>Welche Projektvorlagen werden vom VSSDK bereitgestellt?
 Die beiden Haupttypen von Erweiterungen sind VSPackages und MEF-Erweiterungen. Im Allgemeinen werden VSPackage-Erweiterungen für Erweiterungen verwendet, die Befehle, Toolfenster und Projekte verwenden oder erweitern. MEF-Erweiterungen werden zum Erweitern oder Anpassen des Visual Studio-Editors verwendet.

 Für Visual C- und Visual Basic-Erweiterungen stellt das VSSDK eine leere VSIX-Projektvorlage bereit, die Sie zusammen mit den neuen Elementvorlagen verwenden können, die Menübefehle, Toolfenster und Editorerweiterungen erstellen. Sie können diese Vorlage auch zum Verpacken von Projektvorlagen, Codeausschnitten und anderen Artefakten für die Verteilung an andere Benutzer verwenden.

 Für C++ stellt der VSPackage-Assistent den Code zum Hinzufügen von Menübefehlen, Toolfenstern und benutzerdefinierten Editoren bereit.

 Die Vorlage "Isolierte Shell" wird verwendet, um eine Erweiterung in einer Version der Visual Studio-Shell zu verpacken, die Sie als eigene kennen und verteilen können. Die folgenden Themen zeigen Ihnen, wie Sie mit jeder Art von Erweiterung beginnen:

- Menübefehle: [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)

- Toolfenster: [Erstellen einer Erweiterung mit einem Werkzeugfenster](../extensibility/creating-an-extension-with-a-tool-window.md)

- Editorerweiterungen: [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Grundlegende VSPackages: [Erstellen einer Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX-Projektvorlage: [Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Wie erhalte ich meine Erweiterung so, dass sie wie Visual Studio aussieht?
 Erhalten Sie gute Tipps zum Entwerfen der Benutzeroberfläche für Ihre Erweiterung in [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Wo finde ich Beispiele für VSSDK-Code?
 Jede der im vorherigen Abschnitt aufgeführten Links enthält schrittweise exemplarische Vorgehensweisen, die Ihnen zeigen, wie Sie bestimmte Features implementieren. Sie finden auch Open Source VSSDK-Beispiele auf GitHub unter [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Wie kann ich meine Erweiterung verteilen?
 Sie können Ihre Erweiterung auf einem anderen Computer installieren oder sie als .vsix-Datei an Ihre Freunde senden, die Sie installieren, indem Sie darauf doppelklicken. Weitere Informationen zu VSIX-Paketen finden Sie unter [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md).

 Sie können Ihre Erweiterung auch im Visual Studio Marketplace veröffentlichen, wodurch sie für eine große Anzahl von Visual Studio-Kunden sichtbar wird. Ein Beispiel für das Verpacken einer Erweiterung für den Marketplace finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Weitere Informationen zu den Informationen, die Sie tun müssen, um sie im Marketplace zu veröffentlichen, finden Sie unter [Produkte und Erweiterungen für Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Weitere Informationen

- [Extending Visual Studio for Mac (Erweitern von Visual Studio für Mac)](/visualstudio/mac/extending-visual-studio-mac)
- [Erweitern von Visual Studio-Code](https://code.visualstudio.com/api)
