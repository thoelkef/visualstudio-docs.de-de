---
title: Implementieren von Einzeldatei Generatoren | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9894666dd435dcaa110ba8af8307d7e942119bee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-single-file-generators"></a>Implementieren von Einzeldatei Generatoren
Ein benutzerdefiniertes Tool – auch bezeichnet als eine einzelne Datei-Generator – dienen zum Erweitern der [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projektsysteme in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ein benutzerdefiniertes Tool ist eine COM‑Komponente, implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle. Verwenden diese Schnittstelle, wandelt ein benutzerdefiniertes Tool eine einzelne Eingabedatei in einer einzigen Ausgabedatei an. Das Ergebnis der Transformation werden Quellcode, oder jede andere Ausgabe, die nützlich ist. Zwei Beispiele für benutzerdefinierte Tools generierten Codedateien werden als Reaktion auf Änderungen in einem visuellen Designer und fügt Dateien mithilfe von Web Services Description Language (WSDL) generiert generierten Code.  
  
 Wenn ein benutzerdefiniertes Tool geladen wird, oder die Eingabedatei wird gespeichert, das Projektsystem ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> -Methode, und übergibt einen Verweis auf eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> Rückrufschnittstelle, bei dem das Tool den Status für den Benutzer meldet kann.  
  
 Die Ausgabedatei, die das benutzerdefinierte Tool generiert wird das Projekt mit einer Abhängigkeit der Eingabedatei hinzugefügt. Bestimmt das Projektsystem automatisch der Name der Ausgabedatei, basierend auf von der Implementierung des benutzerdefinierten Tools zurückgegebene Zeichenfolge <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Es muss ein benutzerdefiniertes Tool implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle. Optional, benutzerdefinierte Tools unterstützen die <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> Schnittstelle zum Abrufen von Informationen aus anderen Quellen als der Eingabedatei. In jedem Fall, bevor Sie ein benutzerdefiniertes Tool verwenden können, müssen Sie ihn registrieren mit dem System oder in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokale Registrierung. Weitere Informationen zur Registrierung des benutzerdefinierten Tools finden Sie unter [registrieren Einzeldatei Generatoren](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)