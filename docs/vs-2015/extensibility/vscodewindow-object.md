---
title: Vscodewindow-Objekt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690774"
---
# <a name="vscodewindow-object"></a>VSCodeWindow-Objekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Code Fenster ist ein spezielles Dokument Fenster, das mindestens eine Textansicht enthalten kann, in der Regel das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
 In der Architektur ist das Code Fenster ein Dokument Fenster, das sich innerhalb eines Fensterrahmens befindet. Funktionell ist das Code Fenster einfach ein Dokument Fenster mit zusätzlichen Features. Im MDI-Modus (Multiple Document Interface) ist das Code Fenster der untergeordnete MDI-Frame. Weitere Informationen finden Sie unter [Anpassen von Code Fenstern mit der Legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 In der folgenden Tabelle sind die Schnittstellen des- <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekts enthalten.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Stellt einen generischen Zugriffs Mechanismus bereit, um einen Dienst zu suchen, den eine Globally Unique Identifier (GUID) identifiziert.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Stellt ein untergeordnetes Multiple Document Interface (MDI)-Element dar, das mindestens eine Code Ansicht enthält.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Füllt einen Fensterrahmen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Abbildungen bearbeiten](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
