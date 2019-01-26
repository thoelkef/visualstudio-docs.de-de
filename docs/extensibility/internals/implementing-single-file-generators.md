---
title: Implementieren von Einzeldatei-Generatoren | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3dcc7266bd5e2a7e40c4dfbb4b549c30a1338ae
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942934"
---
# <a name="implementing-single-file-generators"></a>Implementieren von Generatoren einzelner Dateien
Ein benutzerdefiniertes Tool – auch als einen Generator einzelner Dateien bezeichnet – können verwendet werden, um das Erweitern der [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projektsystemen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ein benutzerdefiniertes Tool ist eine COM‑Komponente, implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle. Verwenden diese Schnittstelle, ein benutzerdefiniertes Tool wird eine einzelne Datei in eine einzelne Ausgabedatei transformiert. Das Ergebnis der Transformation für Quellcode werden, oder jede andere Ausgabe, dass dies nützlich ist. Zwei Beispiele für benutzerdefiniertes Tool-generierte Codedateien sind generierten Code in Reaktion auf Änderungen in einem visuellen Designer und Dateien, die mithilfe von Web Services Description Language (WSDL) generiert.  
  
 Wenn ein benutzerdefiniertes Tool geladen wird, oder die Eingabedatei gespeichert wird, wird das Projektsystem ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> -Methode, und übergibt einen Verweis auf eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> Rückrufschnittstelle, bei dem das Tool den Status für den Benutzer meldet kann.  
  
 Die Ausgabedatei, die das benutzerdefinierte Tool generiert wird mit einer Abhängigkeit auf der Eingabedatei zum Projekt hinzugefügt. Das Projektsystem bestimmt automatisch den Namen der Ausgabedatei, basierend auf der Zeichenfolge zurückgegeben, die durch das benutzerdefinierte Tool-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Es muss ein benutzerdefiniertes Tool implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle. Optional können benutzerdefinierte Tools unterstützen die <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> Schnittstelle zum Abrufen von Informationen aus anderen Quellen als Eingabedatei angegeben. In jedem Fall ist, bevor Sie ein benutzerdefiniertes Tool verwenden können, müssen Sie ihn registrieren mit dem System oder in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokale Registrierung. Weitere Informationen zum Registrieren von benutzerdefinierten Tools finden Sie unter [Einzeldatei-Generatoren registrieren](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)