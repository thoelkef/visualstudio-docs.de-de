---
title: 'Vorgehensweise: Festlegen eines Anwendungssymbols (Visual Basic, C#) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bd8616e1f16e12ab07bd30a2d88f728bc79212f6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Vorgehensweise: Festlegen eines Anwendungssymbols (Visual Basic, C#)

Die `Icon`-Eigenschaft für ein Projekt gibt die Symboldatei (*.ico*) an, die für die kompilierte Anwendung im **Datei-Explorer** und in der Windows-Taskleiste angezeigt wird.

Auf die `Icon`-Eigenschaft können Sie im **Projekt-Designer** über den Bereich **Anwendung** zugreifen. Dort finden Sie eine Liste der Symbole, die dem Projekt entweder als Ressourcen oder als Inhaltsdateien hinzugefügt wurden.

> [!NOTE]
> Wenn Sie die Symboleigenschaft für eine Anwendung festgelegt haben, können Sie auch die `Icon`-Eigenschaft für jedes **Fenster** oder **Formular** in der Anwendung festlegen. Informationen zu Fenstersymbolen für eigenständige WPF-Anwendungen (Windows Presentation Foundation) finden Sie unter<xref:System.Windows.Window.Icon%2A>-Eigenschaft.

## <a name="to-specify-an-application-icon"></a>So legen Sie ein Anwendungssymbol fest

1. Wählen Sie im **Projektmappen-Explorer** einen Projektknoten (nicht den Knoten **Projektmappe**) aus.

1. Wählen Sie in der Menüleiste **Projekt** > **Eigenschaften** aus.

1. Wählen Sie, wenn der **Projekt-Designer** angezeigt wird, die Registerkarte **Anwendung** aus.

1. **(Visual Basic)**&mdash;Wählen Sie in der Liste **Symbol** eine Symboldatei (*ICO*-Datei) aus.

    **C#**&mdash; Wählen Sie neben der Liste **Symbol** die Schaltfläche **\<Durchsuchen...>** aus, und navigieren Sie zum Speicherort der gewünschten Symboldatei.

## <a name="see-also"></a>Siehe auch

[Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  
[Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)
