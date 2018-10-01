---
title: Erweitern der Toolbox | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: douge
ms.openlocfilehash: 674b9d1dcebc7ec4a9019c652f0909904fe952c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511424"
---
# <a name="extending-the-toolbox"></a>Erweitern der Toolbox
Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Toolbox** stellt eine Auflistung von Objekten, die, Editoren und Designern über Drag & Drop-Mechanismus der IDE Funktionen bereitstellt.  
  
 Es gibt zwei grundlegende Methoden, die in der kann eine VSPackage mit der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Toolbox**:  
  
-   Ein VSPackage kann neue Datenelemente und Steuerelemente zur **Toolbox**hinzufügen.  
  
-   Ein VSPackage kann ein Ziel oder Consumer vorhandener **Toolbox** -Funktionen sein, das bzw. der die Drag &amp; Drop-Vorgänge sowie das Konfigurieren der Darstellung der **Toolbox**unterstützt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Gewusst wie: Erstellen eines Toolbox-Steuerelements, das Windows Forms verwendet](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Beschreibt das Erstellen eines Toolbox-Steuerelements mithilfe der Vorlage für Toolbox-Steuerelemente von Windows Forms.  
  
 [Erstellen eines WPF-Toolbox-Steuerelements](../extensibility/creating-a-wpf-toolbox-control.md)  
 Beschreibt das Erstellen eines Toolbox-Steuerelements mithilfe der Vorlage für Toolbox-Steuerelemente der WPF.  
  
 [Verwalten der Toolbox](../misc/managing-the-toolbox.md)  
 Beschreibt, wie ein VSPackage den Inhalt und die Darstellung der **Toolbox**verwalten kann.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [How to: Manage the Toolbox Window (Vorgehensweise: Verwalten des Toolbox-Fensters)](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Beschreibt das Arbeiten mit der **Toolbox** in die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE).  
  
 [Vorgehensweise: steuern die Toolbox](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Beschreibt das Verwalten der **Toolbox** mithilfe des Programmiermodells für die Automatisierung.  
  
 [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Dienste zum Erstellen von UI-Elemente, die den Rest der entsprechen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].