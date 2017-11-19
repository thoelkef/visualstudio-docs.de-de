---
title: "Aktualisieren der Benutzeroberfläche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02bf66cba145b1d5fdaea899ca3af4ca2bcefbe1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="updating-the-user-interface"></a>Aktualisieren der Benutzeroberfläche
Nachdem Sie einen Befehl implementiert haben, können Sie Code zum Aktualisieren der Benutzeroberfläche mit dem Status der neuen Befehle hinzufügen.  
  
 In einer normalen Win32-Anwendung der Befehlssatz fortlaufend abgerufen werden kann, und der Status der einzelnen Befehle angepasst werden kann, wie der Benutzer diese anzeigt. Jedoch, da die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell kann als host für eine unbegrenzte Anzahl von VSPackages, umfangreiche Abruf verringern Reaktionsfähigkeit, insbesondere über zwischen verwaltetem Code und COM-Interop-Assemblys abrufen  
  
### <a name="to-update-the-ui"></a>Zum Aktualisieren der Benutzeroberfläche  
  
1.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>-Methode auf.  
  
         Ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle abgerufen werden kann, aus der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> -Dienst wie folgt.  
  
        ```csharp  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         Wenn der Parameter von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> ungleich NULL ist (`TRUE`), und klicken Sie dann das Update, sofort und synchron ausgeführt wird. Es wird empfohlen, wenn Sie 0 (null) übergeben (`FALSE`) für diesen Parameter, um eine gute Leistung zu gewährleisten. Wenn Sie caching vermeiden möchten, wenden Sie die `DontCache` kennzeichnen, wenn Sie den Befehl in der VSCT-Datei erstellen. Verwenden Sie das Flag trotzdem vorsichtig oder möglicherweise zu Leistungseinbußen führen. Weitere Informationen zu Befehlsflags, finden Sie unter der [Flags Befehlselement](../extensibility/command-flag-element.md) Dokumentation.  
  
    -   In VSPackages, auf denen ein ActiveX-Steuerelement mithilfe des Modells für direkte Aktivierung in einem Fenster gehostet wird, ist es möglicherweise einfacher, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> Methode. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> Schnittstelle sind funktional äquivalent. Beide dazu führen, dass die Umgebung den Status aller Befehle erneut abgefragt. In der Regel wird ein Update nicht sofort ausgeführt. Stattdessen wird ein Update erst Leerlaufzeit verzögert. Die Shell speichert der Befehlsstatus um gute Leistung zu gewährleisten. Wenn Sie caching vermeiden möchten, wenden Sie die `DontCache` kennzeichnen, wenn Sie den Befehl in der VSCT-Datei erstellen. Dennoch verwenden Sie das Flag vorsichtig, da die Leistung verringern kann.  
  
         Beachten Sie, die Sie erhalten die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> Schnittstelle durch Aufrufen der `QueryInterface` Methode auf eine <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> -Objekts oder durch Abrufen die Schnittstelle aus der <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> Dienst.  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementation (Implementierung)](../extensibility/internals/command-implementation.md)