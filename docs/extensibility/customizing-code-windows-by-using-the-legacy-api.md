---
title: Anpassen von Codefenster über die Legacy-API | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8284985003415ef3e723fe735e64481c3666180a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109963"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Anpassen von Code-Fenster mit der Legacy-API
Ein Codefenster ist ein Dokumentobjekt für das Fenster, das eine oder mehrere Textansichten unterstützt. Die genaue Features von einem Fenster des Code hängen von dem Dienst zugeordnete Sprache ab. Im Multiple Document Interface (MDI) Modus ist das Codefenster der untergeordneten MDI-Rahmens.  
  
 Codefenster von Sprachdienste gesteuert werden, und jeder Sprachdienst kann eigenen Code-Fenster-Manager bereitstellen. Dadurch wird der Sprachdienst Codefensters, wie z. B. Wellenlinien und farbliche Kennzeichnung von seiner eigenen Zusatzelemente hinzu. Weitere Informationen dazu, wie beim Erstellen eines Fensters Core finden Sie unter [Instanziieren der Core-Editor mithilfe der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Ein Codefenster wird eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> -Objekt, das eine Textansicht und alle Zusatzelemente, in dem Objekt, positioniert wurde. Wenn Sie Fernster des Code-Editor während der Instanziierung des Kerns erstellen, kann Ihre Sprachdienst Anfügen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> in das Codefenster wird wie in der folgenden Abbildung gezeigt.  
  
 ![Grafik zu CodeWindow](../extensibility/media/vscodewindow.gif "Vscodewindow")  
Codefenster  
  
 Der Sprachdienst den Fenster-Manager implementiert und ist zuständig für das Verwalten von randsteuerelementen, z. B. eine Dropdown-Leiste. Ruft der Code-Fenster die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> Methode während der Initialisierung der Code-Fenster. Wenn dieser Aufruf erfolgt, kann der Sprachdienst hinzufügen, eine Dropdownliste Balken- oder wird eine Schaltflächenleiste (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) in das Codefenster.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 `Customizing Code Windows by Using the Legacy API`  
 Erläutert das Codefenster mithilfe der legacy-API anpassen.  
  
 [Vorgehensweise: Hosten einen-Editor in einem anderen Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Erläutert, wie einen zweiten Redakteur in einem Editor-Fenster zu hosten.  
  
 [Vorgehensweise: Ereignisse auszulösen, wenn der Editor den Fokus verliert.](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Erläutert, wie eine Dokumentenansicht an ein dokumentdatenobjekt angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Instanziieren den Core-Editor mithilfe der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Zugreifen auf TheText Ansicht über die Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)