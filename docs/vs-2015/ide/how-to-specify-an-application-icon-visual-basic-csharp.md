---
title: 'Gewusst wie: Angeben eines Anwendungssymbols (Visual Basic, C#) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136fd00bea736af0f0c589c28eae597ff8fd558e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670704"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Gewusst wie: Angeben eines Anwendungssymbols (Visual Basic, C#))
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die `Icon`-Eigenschaft für ein Projekt gibt die Symboldatei (.ico) an, die für die kompilierte Anwendung im Datei-Explorer und in der Windows-Taskleiste angezeigt wird.

 Auf die `Icon`-Eigenschaft können Sie im **Projekt-Designer** über den Bereich **Anwendung** zugreifen. Dort finden Sie eine Liste der Symbole, die dem Projekt entweder als Ressourcen oder als Inhaltsdateien hinzugefügt wurden.

> [!NOTE]
> Wenn Sie die Symboleigenschaft für eine Anwendung festgelegt haben, können Sie auch die `Icon`-Eigenschaft für jedes **Fenster** oder **Formular** in der Anwendung festlegen. Informationen zu Fenstersymbolen für eigenständige WPF-Anwendungen (Windows Presentation Foundation) finden Sie unter<xref:System.Windows.Window.Icon%2A>-Eigenschaft.

### <a name="to-specify-an-application-icon"></a>So legen Sie ein Anwendungssymbol fest

1. Wählen Sie im **Projektmappen-Explorer** einen Projektknoten (nicht den Knoten **Projektmappe**) aus.

2. Wählen Sie in der Menüleiste **Projekt** und **Eigenschaften** aus.

3. Wählen Sie, wenn der **Projekt-Designer** angezeigt wird, die Registerkarte **Anwendung** aus.

4. **(Visual Basic)** Wählen Sie in der Liste **Symbol** eine Symboldatei (.ico) aus.

     **C#** Wählen Sie in der Nähe der Liste **Symbol** die Schaltfläche **\<Durchsuchen...>** aus, und navigieren Sie zum Speicherort der gewünschten Symboldatei.

## <a name="see-also"></a>Siehe auch
 [Anwendungsseite, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [Anwendungsseite, Projekt-C#Designer ()](../ide/reference/application-page-project-designer-csharp.md) [Verwalten von Anwendungseigenschaften](../ide/application-properties.md) Gewusst [wie: Hinzufügen oder Entfernen von Ressourcen](https://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
