---
title: "Schaltflächen im Fenster Eigenschaften | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 950b9f0a7b0f38689042877a42499e23253e6486
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-buttons"></a>Eigenschaften-Fenster-Schaltflächen
Abhängig von der Entwicklungssprache und des Produkttyps bestimmte Schaltflächen angezeigt werden, standardmäßig auf der Symbolleiste für den **Eigenschaften** Fenster. In allen Fällen die **nach Kategorien**, **Alphabetized**, **Eigenschaften**, und **Eigenschaftenseiten** Schaltflächen angezeigt werden. In Visual c# und Visual Basic die **Ereignisse** Schaltfläche wird ebenfalls angezeigt. In bestimmten Visual C++-Projekten die **VC++-Nachrichten** und die **VC überschreibt** Schaltflächen angezeigt werden. Zusätzliche Schaltflächen möglicherweise für andere Projekttypen angezeigt. Weitere Informationen zu den Schaltflächen in der **Eigenschaften** Fenster finden Sie unter [Fenster "Eigenschaften"](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementierung von Eigenschaften im Fenster Schaltflächen  
 Beim Klicken auf die **nach Kategorien** Schaltfläche Aufrufe von Visual Studio die <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> Schnittstelle für das Objekt, das Fokus auf die Eigenschaften nach Kategorie zu sortieren. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>wird implementiert, auf die `IDispatch` -Objekt, das angezeigt wird der **Eigenschaften** Fenster.  
  
 Es gibt 11 vordefinierte Eigenschaftenkategorien, die negative Werte haben. Sie können benutzerdefinierte Kategorien definieren, aber es wird empfohlen, dass Sie positive Werte für die Unterscheidung von vordefinierten Kategorien zuweisen.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Methode gibt den entsprechenden Eigenschaftswert des Kategorie für die angegebene Eigenschaft zurück. Die <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Methode gibt eine Zeichenfolge, die den Namen der Kategorie enthält. Sie müssen sich nur um Unterstützung für benutzerdefinierte Kategoriewerte bereitzustellen, da Visual Studio die Standardeigenschaft Kategoriewerte weiß.  
  
 Beim Klicken auf die **Alphabetized** Schaltfläche, die Eigenschaften werden in alphabetischer Reihenfolge nach Namen angezeigt. Die Namen werden abgerufen, indem `IDispatch` gemäß eines lokalisierten Sortieralgorithmus.  
  
 Wenn die **Eigenschaften** Fenster wird geöffnet, die **Eigenschaften** Schaltfläche wird automatisch angezeigt als ausgewählt. In anderen Teilen der Umgebung, die gleiche Schaltfläche angezeigt wird, und klicken Sie darauf, zum Anzeigen der **Eigenschaften** Fenster.  
  
 Die **Eigenschaftenseiten** Schaltfläche ist nicht verfügbar, wenn `ISpecifyPropertyPages` ist für das ausgewählte Objekt nicht implementiert. Eigenschaftenseiten Anzeige konfigurationsabhängigen Eigenschaften, die in der Regel mit Projektmappen und Projekten verknüpft sind, aber sie kann auch werden Projektelemente (z. B. in Visual C++) zugeordnet.  
  
> [!NOTE]
>  Sie können keine Symbolleistenschaltflächen zum Hinzufügen der **Eigenschaften** Fenster mit nicht verwaltetem Code. Um eine Symbolleisten-Schaltfläche hinzuzufügen, müssen Sie ein verwaltetes Objekt, das von abgeleitet ist erstellen <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)