---
title: Implementieren von Einzeldatei-Generatoren | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956900"
---
# <a name="implementing-single-file-generators"></a>Implementieren von Generatoren einzelner Dateien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein benutzerdefiniertes Tool – auch als einen Generator einzelner Dateien bezeichnet – können verwendet werden, um das Erweitern der [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] und [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Projektsystemen in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Ein benutzerdefiniertes Tool ist eine COM‑Komponente, implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle. Verwenden diese Schnittstelle, ein benutzerdefiniertes Tool wird eine einzelne Datei in eine einzelne Ausgabedatei transformiert. Das Ergebnis der Transformation für Quellcode werden, oder jede andere Ausgabe, dass dies nützlich ist. Zwei Beispiele für benutzerdefiniertes Tool-generierte Codedateien sind generierten Code in Reaktion auf Änderungen in einem visuellen Designer und Dateien, die mithilfe von Web Services Description Language (WSDL) generiert.  
  
 Wenn ein benutzerdefiniertes Tool geladen wird, oder die Eingabedatei gespeichert wird, wird das Projektsystem ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> -Methode, und übergibt einen Verweis auf eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> Rückrufschnittstelle, bei dem das Tool den Status für den Benutzer meldet kann.  
  
 Die Ausgabedatei, die das benutzerdefinierte Tool generiert wird mit einer Abhängigkeit auf der Eingabedatei zum Projekt hinzugefügt. Das Projektsystem bestimmt automatisch den Namen der Ausgabedatei, basierend auf der Zeichenfolge zurückgegeben, die durch das benutzerdefinierte Tool-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Es muss ein benutzerdefiniertes Tool implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle. Optional können benutzerdefinierte Tools unterstützen die <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> Schnittstelle zum Abrufen von Informationen aus anderen Quellen als Eingabedatei angegeben. In jedem Fall ist, bevor Sie ein benutzerdefiniertes Tool verwenden können, müssen Sie ihn registrieren mit dem System oder in der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lokale Registrierung. Weitere Informationen zum Registrieren von benutzerdefinierten Tools finden Sie unter [Einzeldatei-Generatoren registrieren](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Bestimmen die Standard-Namespace eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)
