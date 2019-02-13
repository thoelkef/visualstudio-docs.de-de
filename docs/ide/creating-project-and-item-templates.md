---
title: Vorlagen für Projekte und Dateien
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 603920aac4a7ba6d91996f3717927112ec8e5ec5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933859"
---
# <a name="project-and-item-templates"></a>Projekt- und Elementvorlagen

Projekt- und Elementvorlagen stellen wiederverwendbare Stubs bereit, die Benutzern grundlegenden Code sowie eine grundlegende Struktur vermitteln, die sie an ihre jeweiligen Zwecke anpassen können.

## <a name="visual-studio-templates"></a>Visual Studio-Vorlagen

Zusammen mit Visual Studio wird eine Reihe vordefinierter Projekt- und Elementvorlagen installiert. Beispielsweise handelt es sich bei den Vorlagen für die **Windows Forms-App** und die **Klassenbibliothek** für Visual Basic und C#, die im Dialogfeld **Neues Projekt** dargestellt werden, um Projektvorlagen. Installierte Elementvorlagen werden im Dialogfeld **Neues Element hinzufügen** angezeigt. Sie umfassen Elemente wie Codedateien, XML-Dateien, HTML-Seiten und Stylesheets.

Diese Vorlagen stellen einen Ausgangspunkt bereit, von dem aus Benutzer Projekte erstellen oder vorhandene Projekte erweitern können. Projektvorlagen stellen die Dateien bereit, die für einen bestimmten Projekttyp erforderlich sind; sie umfassen standardmäßige Assemblyverweise und legen standardmäßige Projekteigenschaften und Compileroptionen fest. Elementvorlagen können eine unterschiedliche Komplexität aufweisen. Diese reicht von einer einfachen leeren Datei mit einer bestimmten Erweiterung bis hin zu mehreren Quellcodedateien mit Stubcode, Dateien mit Designer-Informationen und eingebetteten Ressourcen.

Sie können die installierten Vorlagen in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** verwenden, eigene Vorlagen erstellen oder von der Community bereitgestellte Vorlagen herunterladen und verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md) und [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Inhalte einer Vorlage

Alle Projekt- und Elementvorlagen, unabhängig davon, ob diese zusammen mit Visual Studio installiert oder von Ihnen erstellt wurden, funktionieren nach demselben Prinzip und umfassen ähnliche Inhalte. Alle Vorlagen enthalten die folgenden Elemente:

- Die Dateien, die bei Verwendung der Vorlage erstellt werden sollen. In diesen Dateien sind unter anderem Quellcodedateien, eingebettete Ressourcen, Projektdateien enthalten.

- Eine *VSTEMPLATE-Datei*, die die erforderlichen Metadaten zum Anzeigen der Vorlage in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** sowie zum Erstellen eines Projekts oder Elements aus der Vorlage erhält. Weitere Informationen zu *VSTEMPLATE-Dateien* finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).

Wenn diese Dateien in eine *ZIP-Datei* komprimiert sind und sich im richtigen Ordner befinden, werden sie automatisch von Visual Studio an folgenden Orten angezeigt:

- Die Projektvorlagen werden im Dialogfeld **Neues Projekt** angezeigt.

- Die Elementvorlagen werden im Dialogfeld **Neues Element hinzufügen** angezeigt.

Weitere Informationen zu Vorlagenordnern finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)
- [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [Anpassen von Projekt- und Elementvorlagen](../ide/customizing-project-and-item-templates.md)
- [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)