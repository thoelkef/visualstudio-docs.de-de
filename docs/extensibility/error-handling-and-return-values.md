---
title: Fehlerbehandlung und Rückgabewerte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab90fb24820e84f27d67759eb4665d72dffd1aa8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684077"
---
# <a name="error-handling-and-return-values"></a>Fehlerbehandlung und Rückgabewerte
VSPackages und COM-verwenden die gleiche Architektur auf Fehler. Die `SetErrorInfo` und `GetErrorInfo` Funktionen sind Teil der Win32-Anwendungsprogrammierschnittstelle (API). Jedem VSPackage in der integrierten Entwicklungsumgebung (IDE) kann diese globale Win32-APIs, um aussagekräftige Fehlerinformationen Datensatz aufrufen, wenn Sie empfangen eine Fehlermeldung angezeigt. Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] interop-Assemblys zum Verwalten von Fehlerinformationen enthält.

## <a name="interop-methods"></a>Interop-Methoden
 Zur Vereinfachung die IDE bietet eine Methode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, um anstelle der Win32-APIs zu verwenden. In verwaltetem Code verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Wenn ein Fehler `HRESULT` eingeht, auf der Ebene, in dem die Fehlermeldung angezeigt werden soll (Dies ist häufig das Objekt implementieren eine <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Befehlshandler), die IDE verwendet eine andere Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, um das entsprechende Meldung anzuzeigen. Verwalteter Code verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methode.

 Als ein VSPackage-Implementierung, die COM-Objekte normalerweise implementieren `ISupportErrorInfo`. Die `ISupportErrorInfo` Schnittstelle stellt sicher, dass ausführliche Fehlerinformationen der Aufrufkette vertikal verschoben werden kann. Objekte, die auf die Prozesse oder Threads verwendet werden können müssen unterstützen `ISupportErrorInfo` um sicherzustellen, dass die aussagekräftige Fehlerinformationen ordnungsgemäß an den Aufrufer gemarshallt wird.

 Alle Objekte, beziehen sich auf VSPackages und sind beteiligt, Erweitern der IDE, z. B. editorfactorys, Editoren, Hierarchien, und die angebotenen Dienste, sollte ausführliche Fehlerinformationen unterstützen. Während die IDE nicht zum Implementieren dieser VSPackage-Objekten erfordert `ISupportErrorInfo`, es wird immer empfohlen.

 Die IDE ist verantwortlich für Fehlerinformationen reporting und zu einem Benutzer der Anzeige [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] immer ein `HRESULT` an der IDE weitergegeben wird. Die IDE ist auch der Mechanismus zum Erstellen von `ErrorInfo` Objekte.

## <a name="general-guidelines"></a>Allgemeine Richtlinien
 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methoden zum Festlegen und Fehlermeldungen angezeigt werden, die für Ihr VSPackage-Implementierung auch intern sind. Allerdings als in der Regel die folgenden Richtlinien Sie für die Behandlung von Fehlermeldungen in das VSPackage:

-   Implementieren `ISupportErrorInfo` in den VSPackage-COM-Objekten.

-   Erstellen Sie einen Fehlerberichtmechanismus Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> -Methode in der Objekte, implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

-   Lassen Sie die Fehler anzuzeigen, die für Benutzer über die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methode.

## <a name="error-information-in-the-ide"></a>Fehlerinformationen in der IDE
 Die folgenden Regeln anzugeben, das Durchführen von Fehlerinformationen in die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:

-   Wie eine Schutzstrategie, um sicherzustellen, dass veraltete Fehlerinformationen nicht an Benutzer gemeldet werden Funktionen dieser Aufruf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methodenaufruf sollten zunächst die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode. Übergeben Sie `null` zwischengespeicherte Fehlermeldungen zu löschen, vor dem Aufrufen von allen Elementen, die neue Fehlerinformationen festgelegt werden kann.

-   Funktionen, die Fehlermeldungen nicht direkt Berichten dürfen nur zum Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode, wenn sie einen Fehler zurückgeben `HRESULT`. Es ist zulässig, deaktivieren Sie die `ErrorInfo` auf den Eintrag für eine Funktion oder beim Zurückgeben der <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Die einzige Ausnahme dieser Regel wird beim Aufruf einen Fehler zurückgegeben `HRESULT` von dem die empfangende Partei kann explizit wiederherstellen oder ignorieren.

-   Jede Partei, die explizit einen Fehler ignoriert `HRESULT` aufrufen, müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> -Methode mit <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Andernfalls die `ErrorInfo` Objekt möglicherweise versehentlich erneut verwendet werden, wenn eine andere Partei einen Fehler generiert, ohne ihre eigenen `ErrorInfo`.

-   Alle Methoden, die einen Fehler stammen `HRESULT` wird empfohlen, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode, um aussagekräftige Fehlerinformationen bereitzustellen. Wenn das zurückgegebene `HRESULT` ist ein spezieller `FACILITY_ITF` Fehler, und klicken Sie dann auf die Methode ist erforderlich, um eine ordnungsgemäße bieten `ErrorInfo`Objekt. Der zurückgegebene Fehler ist ein standard-Systemfehler (z. B. <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>, usw.) es akzeptabel ist, die den Fehlercode zurück, ohne den expliziten Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode. Als eine defensive Programmierung-Strategie, wenn einen Fehler aus `HRESULT` (einschließlich Systemfehler), rufen Sie immer die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode entweder mit `ErrorInfo` fehlerbeschreibung detaillierter oder `null`.

-   Rufen Sie alle Funktionen, die zurückgeben, ein Fehler verursacht wurde durch einen anderen Aufruf muss auf den Informationen, die von der fehlerhaften empfangen wurde übergeben, in der `HRESULT` ohne Änderung der `ErrorInfo` Objekt.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Component Automation)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
