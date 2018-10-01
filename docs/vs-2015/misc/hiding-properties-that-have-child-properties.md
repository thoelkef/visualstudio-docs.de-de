---
title: Ausblenden von Eigenschaften, die untergeordneten Eigenschaften | Microsoft-Dokumentation
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
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: bd340b748311bbb257ed0c4bbfe7b972cbf7beb9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521205"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ausblenden von Eigenschaftenfenster mit untergeordneten Eigenschaften
Sie sollten, um Eigenschaften auszublenden, die untergeordneten Eigenschaften:  
  
-   Wenn Sie geschachtelte Projekte verfügen, in denen steuert des übergeordnete Projekts programmgesteuert einige Aspekte des untergeordneten Projekts.  
  
-   Wenn Sie ein Steuerelement mit eines spezialisierten Designers verwenden, und Sie sich nicht um Entwicklern die Vollzugriff auf alle Eigenschaften des Steuerelements möchten.  
  
-   Wenn Sie Bereich eines Objekts Besitzer und das Anzeigen der Eigenschaften einschränken möchten.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Um Eigenschaften auszublenden, die untergeordneten Eigenschaften  
  
1.  Legen Sie die `pfDisplay` Parameter im <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> zu `FALSE`.  
  
2.  Legen Sie die `pfHide` Parameter im <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> zu `TRUE`.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigeraster für Eigenschaften](../extensibility/internals/properties-display-grid.md)