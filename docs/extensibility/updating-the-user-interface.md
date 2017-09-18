---
title: "Aktualisieren der Benutzeroberfl&#228;che | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aktualisieren von Benutzeroberflächen"
  - "Befehle, Aktualisieren der UI"
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 41
---
# Aktualisieren der Benutzeroberfl&#228;che
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nachdem Sie einen Befehl implementiert haben, können Sie Code zum Aktualisieren der Benutzeroberfläche mit dem Status des neuen Befehle hinzufügen.  
  
 In einer normalen Win32\-Anwendung der Befehlssatz fortlaufend abgerufen werden kann, und der Status der einzelnen Befehle angepasst werden kann, wie der Benutzer diese anzeigt. Aber da die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell kann als host für eine unbegrenzte Anzahl von VSPackages, umfangreiche Abruf verringert möglicherweise die Reaktionsfähigkeit, insbesondere über zwischen verwaltetem Code und COM\-Interop\-Assemblys abrufen  
  
### Zum Aktualisieren der Benutzeroberfläche  
  
1.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>\-Methode auf.  
  
         Eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle abgerufen werden kann, aus der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service wie folgt.  
  
        ```c#  
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
  
         Wenn der Parameter der der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> ungleich Null \(`TRUE`\), und klicken Sie dann die Aktualisierung synchron und sofort ausgeführt wird. Es wird empfohlen, Sie 0 \(NULL übergeben\) \(`FALSE`\) für diesen Parameter, um gute Leistung aufrechtzuerhalten. Wenn Sie caching vermeiden möchten, wenden Sie die `DontCache` kennzeichnen, wenn Sie den Befehl in der VSCT\-Datei erstellen. Verwenden Sie das Flag dennoch mit Vorsicht oder möglicherweise die Leistung verringern. Weitere Informationen zu Befehlsflags, finden Sie unter der [Command\-Flag\-Element](../extensibility/command-flag-element.md) Dokumentation.  
  
    -   In VSPackages, auf denen ein ActiveX\-Steuerelement mithilfe der direkte Aktivierung des Modells in einem Fenster gehostet wird, ist es möglicherweise einfacher, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> Methode. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> \-Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> \-Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> Schnittstelle sind funktional äquivalent. Beide bewirken, dass die Umgebung, um den Status aller Befehle erneut abzufragen. Ein Update wird in der Regel nicht sofort ausgeführt. Stattdessen wird ein Update Leerlaufzeit verzögert. Die Shell speichert der Befehlsstatus um gute Leistung zu gewährleisten. Wenn Sie caching vermeiden möchten, wenden Sie die `DontCache` kennzeichnen, wenn Sie den Befehl in der VSCT\-Datei erstellen. Dennoch verwenden Sie das Flag mit Vorsicht, da die Leistung verringern kann.  
  
         Beachten, die Sie erhalten, können Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> Schnittstelle durch Aufrufen der `QueryInterface` \-Methode für ein <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> Objekt oder durch Abrufen die Schnittstelle aus der <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> Service.  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementierung](../extensibility/internals/command-implementation.md)