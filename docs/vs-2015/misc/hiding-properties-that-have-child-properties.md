---
title: Ausblenden von Eigenschaften, die untergeordneten Eigenschaften | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052362"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ausblenden von Eigenschaftenfenster mit untergeordneten Eigenschaften
Sie sollten, um Eigenschaften auszublenden, die untergeordneten Eigenschaften:  
  
- Wenn Sie geschachtelte Projekte verfügen, in denen steuert des übergeordnete Projekts programmgesteuert einige Aspekte des untergeordneten Projekts.  
  
- Wenn Sie ein Steuerelement mit eines spezialisierten Designers verwenden, und Sie sich nicht um Entwicklern die Vollzugriff auf alle Eigenschaften des Steuerelements möchten.  
  
- Wenn Sie Bereich eines Objekts Besitzer und das Anzeigen der Eigenschaften einschränken möchten.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Um Eigenschaften auszublenden, die untergeordneten Eigenschaften  
  
1. Legen Sie die `pfDisplay` Parameter im <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> zu `FALSE`.  
  
2. Legen Sie die `pfHide` Parameter im <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> zu `TRUE`.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigeraster für Eigenschaften](../extensibility/internals/properties-display-grid.md)