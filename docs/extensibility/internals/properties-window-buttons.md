---
title: "Eigenschaften-Fenster-Schaltfl&#228;chen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Im Eigenschaftenfenster für Schaltflächen"
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Eigenschaften-Fenster-Schaltfl&#228;chen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abhängig von der Entwicklungssprache und dem Produkt " werden standardmäßig auf bestimmte Schaltflächen der Symbolleiste für das **Eigenschaften** Fenster angezeigt.  In allen Fällen werden die **Nach Kategorien**, **Alphabetisch sortiert**, **Eigenschaften**und **Eigenschaftenseiten** Schaltflächen angezeigt.  In Visual C\# und Visual Basic wird die **Ereignisse** Schaltfläche ebenfalls angezeigt.  In einigen Visual C\+\+\-Projekten werden **VC\+\+\-Meldungen** und die **VC\-Überschreibungen** Schaltflächen angezeigt.  Zusätzliche Schaltflächen sind für den Knoten Andere Projekttypen angezeigt werden.  Weitere Informationen über die Schaltflächen im Fenster **Eigenschaften** finden Sie unter [Eigenschaftenfenster](../../ide/reference/properties-window.md).  
  
## Implementierung von Eigenschaftenfenster\-Schaltflächen  
 Wenn Sie auf die **Nach Kategorien** Schaltfläche klicken, ruft Visual Studio die <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>\-Schnittstelle für das Objekt auf, das den Fokus besitzt, um die Eigenschaften nach Kategorien zu sortieren.  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> wird auf dem `IDispatch`\-Objekt implementiert, das dem **Eigenschaften** Fenster dargestellt wird.  
  
 Es gibt 11 Basiseigenschaft Kategorien mit negativen Werten.  Sie können benutzerdefinierte Kategorien definieren, aber wir empfehlen, dass Sie ihnen positive Werte zuweisen, damit sie von den vordefinierten Kategorien unterscheiden.  
  
 Die Methode <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Kategorien Eigenschaft gibt den entsprechenden Wert für die angegebene Eigenschaft zurück.  Die <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>\-Methode gibt eine Zeichenfolge zurück, die den Kategorienamen enthält.  Sie müssen die Unterstützung für benutzerdefinierte Kategorien nur Werte bereitstellen, da Visual Studio die Kategorien für Attributwerte kennt.  
  
 Wenn Sie auf die **Alphabetisch sortiert** Schaltfläche klicken, werden die Eigenschaften nach Namen in alphabetischer Reihenfolge angezeigt.  Die Namen werden durch `IDispatch` in einem isolierten Sortieralgorithmus abgerufen.  
  
 Wenn das **Eigenschaften** Fenster geöffnet wird, wird die Schaltfläche **Eigenschaften** automatisch als ausgewählt angezeigt.  In anderen Teilen der Umgebung, wird die gleiche Schaltfläche angezeigt, und Sie können darauf klicken, um das **Eigenschaften** Fenster anzuzeigen.  
  
 Die **Eigenschaftenseiten** Schaltfläche ist nicht verfügbar, wenn `ISpecifyPropertyPages` nicht für das ausgewählte Objekt implementiert wird.  Eigenschaftenseiten wird anlagenabhängige Eigenschaften an, die in der Regel mit Projektmappen und Projekten zugeordnet sind, sie können aber auch sein werden Projektelemente zugeordnet ist \(z. B. in Visual C\+\+\)  
  
> [!NOTE]
>  Sie können im Fenster **Eigenschaften** nicht Symbolleisten\-Schaltflächen hinzufügen, indem Sie nicht verwaltetem Code verwenden.  Um eine Symbolleisten\-Schaltfläche hinzuzufügen, müssen Sie ein verwaltetes Objekt erstellen, das von <xref:System.Windows.Forms.Design.PropertyTab>berechnet.  
  
## Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)