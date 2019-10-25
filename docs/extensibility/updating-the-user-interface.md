---
title: Aktualisieren der Benutzeroberfläche | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf41a41e68aa73e07bdcafe8bcdcd335fff6e6eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718783"
---
# <a name="updating-the-user-interface"></a>Aktualisieren der Benutzeroberfläche
Nachdem Sie einen Befehl implementiert haben, können Sie Code hinzufügen, um die Benutzeroberfläche mit dem Zustand ihrer neuen Befehle zu aktualisieren.

 In einer typischen Win32-Anwendung kann der Befehlssatz fortlaufend abgepolgt werden, und der Zustand einzelner Befehle kann angepasst werden, wenn Sie vom Benutzer angezeigt werden. Da die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell jedoch eine unbegrenzte Anzahl von VSPackages hosten kann, kann das umfangreiche abrufen die Reaktionsfähigkeit verringern, insbesondere das Abrufen von Interop-Assemblys zwischen verwaltetem Code und com.

### <a name="to-update-the-ui"></a>So aktualisieren Sie die Benutzeroberfläche

1. Führen Sie einen der folgenden Schritte aus:

    - Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>-Methode auf.

         Eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>-Schnittstelle kann wie folgt vom <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>-Dienst abgerufen werden.

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

         Wenn der-Parameter der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> nicht NULL (`TRUE`) ist, wird das Update synchron und sofort ausgeführt. Es wird empfohlen, NULL (`FALSE`) für diesen Parameter zu übergeben, um eine gute Leistung zu gewährleisten. Wenn Sie das Caching vermeiden möchten, wenden Sie das `DontCache`-Flag an, wenn Sie den Befehl in der vsct-Datei erstellen. Verwenden Sie das Flag trotzdem vorsichtig, oder die Leistung kann abnehmen. Weitere Informationen zu Befehlsflags finden Sie in der Dokumentation zum [Befehlsflag](../extensibility/command-flag-element.md) .

    - In VSPackages, die ein ActiveX-Steuerelement mithilfe des direkten Aktivierungs Modells in einem Fenster hosten, ist es möglicherweise bequemer, die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>-Methode zu verwenden. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>-Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>-Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>-Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>-Schnittstelle sind funktional äquivalent. Beide bewirken, dass die Umgebung den Status aller Befehle erneut abfragt. In der Regel wird ein Update nicht sofort ausgeführt. Stattdessen wird ein Update bis zur Leerlaufzeit verzögert. Die Shell speichert den Befehls Zustand zwischen, um eine gute Leistung zu gewährleisten. Wenn Sie das Caching vermeiden möchten, wenden Sie das `DontCache`-Flag an, wenn Sie den Befehl in der vsct-Datei erstellen. Verwenden Sie das Flag trotzdem vorsichtig, da sich die Leistung möglicherweise verringert.

         Beachten Sie, dass Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>-Schnittstelle abrufen können, indem Sie die `QueryInterface`-Methode für ein <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> Objekt aufrufen, oder indem Sie die Schnittstelle vom <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> Dienst abrufen.

## <a name="see-also"></a>Siehe auch
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementation (Implementierung)](../extensibility/internals/command-implementation.md)