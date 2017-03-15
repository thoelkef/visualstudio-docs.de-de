---
title: "Ausblenden von Eigenschaftenfenster mit untergeordneten Eigenschaften | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eigenschaften [Visual Studio SDK], ausblenden"
  - "Eigenschaftenfenster, Eigenschaften mit untergeordneten Eigenschaften ausblenden"
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Ausblenden von Eigenschaftenfenster mit untergeordneten Eigenschaften
Sie können Eigenschaften ausgeblendet werden, die über untergeordnete Eigenschaften besitzen:  
  
-   Wenn Sie Projekte geschachtelt haben, in denen das übergeordnete Projekt programmgesteuert einige Aspekte des untergeordneten Projekts gesteuert wird.  
  
-   Wenn Sie ein Steuerelement mit einem spezialisierten Designers und Sie möchten nicht Entwicklern den Zugriff auf alle Eigenschaften des Steuerelements geben.  
  
-   Wenn Sie Bereichs besitz eines Objekts aufweisen und die Ansicht von Eigenschaften einschränken möchten.  
  
### So blenden Sie Eigenschaften mit untergeordneten Eigenschaften  
  
1.  Legen Sie den `pfDisplay`\-Parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> zu `FALSE`fest.  
  
2.  Legen Sie den `pfHide`\-Parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> zu `TRUE`fest.  
  
## Siehe auch  
 [Raster von Eigenschaften anzeigen](../extensibility/internals/properties-display-grid.md)