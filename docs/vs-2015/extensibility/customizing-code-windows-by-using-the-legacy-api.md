---
title: Anpassen von Code Fenstern mithilfe der Legacy-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556131"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Anpassen von Codefenstern mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Code Fenster ist ein Dokument Fenster Objekt, das mindestens eine Textansicht unterstützt. Die genauen Features eines Code Fensters hängen vom zugeordneten Sprachdienst ab. Im MDI-Modus (Multiple Document Interface) ist das Code Fenster der untergeordnete MDI-Frame.  
  
 Code Fenster werden von Sprachdiensten gesteuert, und jeder Sprachdienst kann seinen eigenen Code Fenster-Manager bereitstellen. Dadurch kann der Sprachdienst dem Code Fenster seine eigenen Zusatzelemente hinzufügen, z. b. Wellenlinien, farbige Farbgebung usw. Weitere Informationen zum Erstellen eines Kern Fensters finden Sie unter [Instanziieren des Kern Editors mithilfe der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Ein Code Fenster ist ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Objekt, das eine Textansicht und alle Zusatzelemente enthält, die im-Objekt vorhanden sind. Wenn Sie das Code Fenster während der Instanziierung des Kern-Editors erstellen, kann Ihr Sprachdienst ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> an das Code Fenster anfügen, wie in der folgenden Abbildung dargestellt.  
  
 ![Grafik zu CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow beteiligt ist")  
Codefenster  
  
 Der Sprachdienst implementiert den Code Fenster-Manager und ist für die Verwaltung von Zusatzelementen, z. b. einer Dropdown Leiste, zuständig. Das Code Fenster ruft <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> während der Code Fenster Initialisierung die-Methode auf. Wenn dieser Aufrufe erfolgt, kann der Sprachdienst dem Code Fenster eine Dropdown Leiste oder eine Schaltflächen Leiste () hinzufügen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient> .  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 `Customizing Code Windows by Using the Legacy API`  
 Erläutert, wie Code Fenster mithilfe der Legacy-API angepasst werden.  
  
 [Vorgehensweise: Hosten eines Editors in einem anderen Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Erläutert, wie ein zweiter Editor in einem Editor-Fenster gehostet wird.  
  
 [Vorgehensweise: Auslösen von Ereignissen, wenn der Editor den Fokus verliert](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Erläutert das Anfügen einer Dokument Ansicht an ein Dokument Datenobjekt.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Instanziieren des Kern Editors mithilfe der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Zugriff auf die Textansicht mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
