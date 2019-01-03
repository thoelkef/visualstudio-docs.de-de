---
title: Aktualisieren der Benutzeroberfläche | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f4cbc2deb6f292bf188109bcf8e012f7925cdea8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887983"
---
# <a name="updating-the-user-interface"></a>Aktualisieren der Benutzeroberfläche
Nachdem Sie einen Befehl implementiert haben, können Sie Code zum Aktualisieren der Benutzeroberfläche mit dem Status der Ihre neue Befehle hinzufügen.  
  
 In einer typischen Win32-Anwendung der Befehlssatz ständig abgefragt werden kann, und der Status der einzelnen Befehle angepasst werden kann, wie die Benutzer diese anzeigt. Aber da die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell kann eine unbegrenzte Anzahl von VSPackages, umfangreiche Abruf verringert möglicherweise die Reaktionsfähigkeit, insbesondere über zwischen verwaltetem Code und COM-interop-Assemblys abrufen  
  
### <a name="to-update-the-ui"></a>Zur Aktualisierung der Benutzeroberfläche  
  
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
  
         Wenn der Parameter, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> ungleich NULL ist (`TRUE`), und klicken Sie dann das Update synchron und sofort ausgeführt wird. Es wird empfohlen, Sie 0 (NULL übergeben) (`FALSE`) für diesen Parameter, um sicherzustellen, dass eine guten Leistung. Wenn Sie die Zwischenspeicherung vermeiden möchten, wenden Sie die `DontCache` zu kennzeichnen, wenn Sie den Befehl in der VSCT-Datei erstellen. Dennoch das Flag mit Vorsicht verwenden, oder kann die Leistung verringern. Weitere Informationen zu Befehlsflags, finden Sie unter den [Commandflag-Element](../extensibility/command-flag-element.md) Dokumentation.  
  
    -   In VSPackages, auf denen ein ActiveX-Steuerelement mit dem direkten Aktivierung-Modell in einem Fenster gehostet wird, ist es möglicherweise bequemer, mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> Methode. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> -Methode in der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> -Methode in der die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> Schnittstelle sind funktional äquivalent. Beide dazu führen, dass die Umgebung den Status aller Befehle erneut abfragen. In der Regel wird ein Update nicht sofort ausgeführt werden. Stattdessen wird ein Update Leerlaufzeit verzögert. Die Shell speichert der Befehlsstatus, um sicherzustellen, dass eine guten Leistung. Wenn Sie die Zwischenspeicherung vermeiden möchten, wenden Sie die `DontCache` zu kennzeichnen, wenn Sie den Befehl in der VSCT-Datei erstellen. Dennoch verwenden Sie das Flag mit Vorsicht, da die Leistung verringern kann.  
  
         Beachten Sie, die Sie erhalten die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> Schnittstelle durch Aufrufen der `QueryInterface` Methode für ein <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> Objekt oder durch Abrufen der Schnittstelle vom die <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> Service.  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementation (Implementierung)](../extensibility/internals/command-implementation.md)