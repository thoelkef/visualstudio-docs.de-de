---
title: Aktualisieren der Benutzeroberfläche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698885"
---
# <a name="updating-the-user-interface"></a>Aktualisieren der Benutzeroberfläche
Nachdem Sie einen Befehl implementiert haben, können Sie Code hinzufügen, um die Benutzeroberfläche mit dem Status der neuen Befehle zu aktualisieren.

 In einer typischen Win32-Anwendung kann der Befehlssatz kontinuierlich abgefragt und der Status einzelner Befehle angepasst werden, wenn der Benutzer sie anzeigt. Da die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell jedoch eine unbegrenzte Anzahl von VSPackages hosten kann, können umfangreiche Abfragen die Reaktionsfähigkeit verringern, insbesondere die Abfrage über Interopassemblys zwischen verwaltetem Code und COM.

### <a name="to-update-the-ui"></a>So aktualisieren Sie die Benutzeroberfläche

1. Führen Sie einen der folgenden Schritte aus:

    - Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> -Methode auf.

         Eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle kann wie <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> folgt vom Dienst abgerufen werden.

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

         Wenn der Parameter <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> des Werts`TRUE`ungleich Null ist ( ), wird die Aktualisierung synchron und sofort durchgeführt. Es wird empfohlen,`FALSE`dass Sie Null ( ) für diesen Parameter übergeben, um eine gute Leistung zu erhalten. Wenn Sie zwischenspeichern möchten, `DontCache` wenden Sie das Flag an, wenn Sie den Befehl in der .vsct-Datei erstellen. Verwenden Sie die Flagge jedoch vorsichtig, oder die Leistung kann abnehmen. Weitere Informationen zu Befehlsflags finden Sie in der Dokumentation [zum Befehlsflagelementelement.](../extensibility/command-flag-element.md)

    - In VSPackages, die ein ActiveX-Steuerelement mithilfe des ortsgesteuerten Aktivierungsmodells in <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> einem Fenster hosten, ist es möglicherweise bequemer, die Methode zu verwenden. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> in der <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> und die Methode in der Schnittstelle sind funktional gleichwertig. Beide bewirken, dass die Umgebung den Status aller Befehle erneut abfragt. In der Regel wird eine Aktualisierung nicht sofort durchgeführt. Stattdessen wird eine Aktualisierung auf die Leerlaufzeit verzögert. Die Shell speichert den Befehlsstatus zwischen, um eine gute Leistung zu erhalten. Wenn Sie zwischenspeichern möchten, `DontCache` wenden Sie das Flag an, wenn Sie den Befehl in der .vsct-Datei erstellen. Verwenden Sie die Flagge jedoch vorsichtig, da die Leistung abnehmen kann.

         Beachten Sie, dass <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> Sie die `QueryInterface` Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> abrufen können, indem Sie <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> die Methode für ein Objekt aufrufen oder die Schnittstelle vom Dienst abrufen.

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementierung](../extensibility/internals/command-implementation.md)
