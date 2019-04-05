---
title: Erweitern der Toolbox | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: jillfra
ms.openlocfilehash: a1cf66baf73fe4a04dcb21b0c7ac7609214bea20
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959512"
---
# <a name="extending-the-toolbox"></a>Erweitern der Toolbox
Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Toolbox** stellt eine Auflistung von Objekten bereit, die Editoren und Designern über den Drag & Drop-Mechanismus der IDE Funktionen bereitstellt.  
  
 Es gibt zwei grundlegende Methoden, wie ein VSPackage mit der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Toolbox**arbeitet:  
  
-   Ein VSPackage kann neue Datenelemente und Steuerelemente zur **Toolbox**hinzufügen.  
  
-   Ein VSPackage kann ein Ziel oder Consumer vorhandener **Toolbox** -Funktionen sein, das bzw. der die Drag &amp; Drop-Vorgänge sowie das Konfigurieren der Darstellung der **Toolbox**unterstützt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorgehensweise: Erstellen eines Toolbox-Steuerelements, das Windows Forms verwendet](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Beschreibt das Erstellen eines Toolbox-Steuerelements mithilfe der Vorlage für Toolbox-Steuerelemente von Windows Forms.  
  
 [Erstellen eines WPF-Toolbox-Steuerelements](../extensibility/creating-a-wpf-toolbox-control.md)  
 Beschreibt das Erstellen eines Toolbox-Steuerelements mithilfe der Vorlage für Toolbox-Steuerelemente der WPF.  
  
 [Verwalten der Toolbox](../misc/managing-the-toolbox.md)  
 Beschreibt, wie ein VSPackage den Inhalt und die Darstellung der **Toolbox**verwalten kann.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Vorgehensweise: Verwalten des Toolbox-Fensters](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Beschreibt die Arbeit mit der **Toolbox** in der integrierten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Entwicklungsumgebung (IDE).  
  
 [Vorgehensweise: Steuern der Toolbox](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Beschreibt das Verwalten der **Toolbox** mithilfe des Programmiermodells für die Automatisierung.  
  
 [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Dienste zum Erstellen von Benutzeroberflächenelementen verwendet werden, die zu den übrigen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Komponenten passen.