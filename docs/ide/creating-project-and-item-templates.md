---
title: Visual Studio-Vorlagen für Projekte und Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 900b750df391029a1bed15b2da003f94c085148a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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

## <a name="starter-kits"></a>Starter Kits

Starter Kits sind erweiterte Vorlagen, die mit anderen Mitgliedern der Community gemeinsam genutzt werden können. Starter Kits enthalten kompilierbare Codebeispiele, Dokumentationen und andere Ressourcen, die den Benutzern den Einstieg in neue Tools und Programmiertechniken erleichtern, während diese nützliche und reale Anwendungen erstellen. Die grundlegende Inhalte und Verfahren für Starter Kits sind identisch mit denen für Vorlagen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Starter Kits](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Siehe auch

[Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)  
[Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)  
[Vorlagenparameter](../ide/template-parameters.md)  
[Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)  
[NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)