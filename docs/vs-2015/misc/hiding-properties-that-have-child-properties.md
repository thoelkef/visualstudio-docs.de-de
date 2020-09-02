---
title: Ausblenden von Eigenschaften mit untergeordneten Eigenschaften | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822385"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ausblenden von Eigenschaftenfenster mit untergeordneten Eigenschaften
Sie sollten Eigenschaften ausblenden, die untergeordnete Eigenschaften aufweisen:  
  
- Wenn Sie über ein Projekt verfügen, in dem das übergeordnete Projekt einige Aspekte des untergeordneten Projekts Programm gesteuert steuert.  
  
- Wenn Sie ein-Steuerelement mit einem spezialisierten Designer verwenden und Sie Entwicklern keinen Vollzugriff auf alle Eigenschaften des-Steuer Elements bieten möchten.  
  
- Wenn Sie den Gültigkeitsbereich eines Objekts besitzen und die Ansicht der Eigenschaften einschränken möchten.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>So blenden Sie Eigenschaften mit untergeordneten Eigenschaften aus  
  
1. Legen Sie den- `pfDisplay` Parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> auf fest `FALSE` .  
  
2. Legen Sie den- `pfHide` Parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> auf fest `TRUE` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigeraster für Eigenschaften](../extensibility/internals/properties-display-grid.md)