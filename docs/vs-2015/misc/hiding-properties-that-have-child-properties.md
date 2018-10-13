---
title: Ausblenden von Eigenschaften, die untergeordneten Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 76ef9c093bb91bc3cc22df7b56c4d5d69dbc41a5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196520"
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