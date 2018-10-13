---
title: Anpassen von Windows von Code mithilfe der Legacy-API | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c698f9661866ad6d2900bb7feb0f0f4a17d21589
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299987"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Anpassen von Windows von Code mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Codefenster ist ein Dokument Window-Objekt, das eine oder mehrere Textansichten unterstützt. Die exakten Features eines Codefensters hängen von dem Dienst zugeordnete Sprache ab. Im Modus "Multiple Document Interface (MDI)" ist im Code-Fenster den MDI-Child-Rahmen.  
  
 Codefenster mit Sprachdienste gesteuert, und jeder Sprachdienst kann eigene Codefenster-Manager bereitstellen. Dadurch wird den Sprachdienst einen eigenen Zusatzelemente, die im Code-Fenster, z. B. Wellenlinien, Farbgebung und mehr hinzu. Weitere Informationen dazu, wie beim Erstellen eines Fensters Core finden Sie unter [Instanziieren der Kern-Editor durch Verwenden der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Ein Codefenster ist ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> -Objekt, das eine Textansicht und alle Zusatzelemente, die im-Objekt positioniert ist. Wenn Sie im Code-Fenster während der Instanziierung des den Kern-Editor erstellen, kann der Sprachdienst Anfügen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> zum Code-Fenster, wie in der folgenden Abbildung gezeigt wird.  
  
 ![CodeWindow-Grafik](../extensibility/media/vscodewindow.gif "Vscodewindow")  
Codefenster  
  
 Der Sprachdienst den Codefenster-Manager implementiert und ist verantwortlich für die Verwaltung der Zusatzelemente, wie eine Dropdownleiste. Ruft der Code-Fenster die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> Methode während der Initialisierung der Code-Fenster. Wenn dieser Aufruf erfolgt, kann der Sprachdienst hinzufügen, eine Dropdownleiste oder eine Schaltflächenleiste (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) zum Code-Fenster.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 `Customizing Code Windows by Using the Legacy API`  
 Erläutert das Anpassen des Code-Fenster mit der legacy-API.  
  
 [Vorgehensweise: Hosten eines Editors in einem anderen Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Erläutert, wie einen zweiten Redakteur in einem Editor-Fenster zu hosten.  
  
 [Vorgehensweise: Auslösen von Ereignissen, wenn der Editor den Fokus verliert](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Erläutert, wie eine Dokumentenansicht an ein dokumentdatenobjekt angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Instanziieren die Kern-Editor mit der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Zugriff auf die Textansicht mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

