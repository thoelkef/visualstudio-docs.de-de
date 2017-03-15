---
title: "Verwenden des Farbverlaufsdiensts in einem Toolfenster | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dienste, exemplarische Vorgehensweisen"
  - "Toolfenster, Farbverlaufsdienst"
  - "Farbverlaufsdienst, exemplarische Vorgehensweisen"
  - "Dienste, verarbeiten"
ms.assetid: 67590982-6e1f-4e4b-be18-7d1b294cabff
caps.latest.revision: 44
caps.handback.revision: 44
manager: "douge"
---
# Verwenden des Farbverlaufsdiensts in einem Toolfenster
Da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Toolfenster mit Windows Presentation Foundation \(WPF\) erstellt wurden, müssen Sie den Farbverlauf für den Code nicht aufrufen.  Stattdessen im Designer, der die Toolfenster Oberfläche darstellt, wählen Sie das Element, und klicken Sie dann `StackPanel` im Fenster **Eigenschaften** , ändern Sie die **Hintergrund** Eigenschaft, um den Farbverlauf festzulegen.  Weitere Informationen finden Sie unter [Festlegen von Farben, Farbverläufen und Deckkraft](../misc/setting-colors-gradients-and-opacity.md).  
  
## Siehe auch  
 [NOT IN BUILD: Tool Window Walkthroughs](http://msdn.microsoft.com/de-de/ecffc579-0e96-48ad-90f3-01a3d80f3ce5)   
 [Erweitern von Toolfenstern](../misc/extending-tool-windows.md)   
 [Festlegen von Farben, Farbverläufen und Deckkraft](../misc/setting-colors-gradients-and-opacity.md)