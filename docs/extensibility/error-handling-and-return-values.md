---
title: Fehlerbehandlung und Rückgabewerte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711937"
---
# <a name="error-handling-and-return-values"></a>Fehlerbehandlung und Rückgabevonwerte
VSPackages und COM verwenden dieselbe Architektur für Fehler. Die `SetErrorInfo` `GetErrorInfo` und Funktionen sind Teil der Win32 Application Programming Interface (API). Jedes VSPackage in der integrierten Entwicklungsumgebung (IDE) kann diese globalen Win32-APIs aufrufen, um umfangreiche Fehlerinformationen aufzuzeichnen, wenn eine Fehlerbenachrichtigung empfangen wird. Der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] stellt Interopassemblys zum Verwalten von Fehlerinformationen bereit.

## <a name="interop-methods"></a>Interop-Methoden
 Als Annehmlichkeit stellt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>IDE eine Methode bereit, die verwendet werden soll, anstatt die Win32-APIs aufzurufen. Verwenden Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>in verwaltetem Code . Wenn ein `HRESULT` Fehler auf der Ebene eintrifft, auf der die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Fehlermeldung angezeigt werden soll (dies ist häufig das Objekt, das einen Befehlshandler implementiert), verwendet die IDE eine andere Methode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>um das entsprechende Meldungsfeld anzuzeigen. Verwenden Sie in <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> verwaltetem Code die Methode.

 Als VSPackage-Implementierer implementieren `ISupportErrorInfo`Ihre COM-Objekte normalerweise . Die `ISupportErrorInfo` Schnittstelle stellt sicher, dass umfangreiche Fehlerinformationen vertikal in der Aufrufkette nach oben verschoben werden können. Objekte, die prozess- oder über `ISupportErrorInfo` Threads hinweg verwendet werden können, müssen unterstützen, um sicherzustellen, dass die umfangreichen Fehlerinformationen ordnungsgemäß an den Aufrufer zurückgemarshallt werden.

 Alle Objekte, die sich auf VSPackages beziehen und an der Erweiterung der IDE beteiligt sind, einschließlich Editorfactorys, Editoren, Hierarchien und angebotenen Diensten, sollten umfangreiche Fehlerinformationen unterstützen. Während die IDE diese VSPackage-Objekte `ISupportErrorInfo`nicht implementieren muss, wird sie immer empfohlen.

 Die IDE ist dafür verantwortlich, Fehlerinformationen zu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] melden `HRESULT` und sie einem Benutzer anzuzeigen, wenn ein an die IDE weitergegeben wird. Die IDE ist auch `ErrorInfo` der Mechanismus zum Erstellen von Objekten.

## <a name="general-guidelines"></a>Allgemeine Richtlinien
 Sie können <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> und Methoden verwenden, um Fehler festzulegen und zu melden, die auch intern in Ihrer VSPackage-Implementierung sind. Befolgen Sie jedoch in der Regel die folgenden Richtlinien für die Behandlung von Fehlermeldungen in Ihrem VSPackage:

- Implementieren `ISupportErrorInfo` Sie in Ihren VSPackage COM-Objekten.

- Erstellen Sie einen Fehlerberichterstattungsmechanismus, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode in Objekten aufruft, die implementieren. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>

- Lassen Sie die IDE Fehler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> für Benutzer über die Methode anzeigen.

## <a name="error-information-in-the-ide"></a>Fehlerinformationen in der IDE
 Die folgenden Regeln geben an, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wie Fehlerinformationen in der IDE behandelt werden:

- Als defensive Strategie, um sicherzustellen, dass veraltete Fehlerinformationen nicht <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> an Benutzer <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> gemeldet werden, sollten Funktionen, die die Methode aufrufen, zuerst die Methode aufrufen. Übergeben `null` Sie die Zwischenrufe, bevor Sie irgendetwas aufrufen, das möglicherweise neue Fehlerinformationen setzt.

- Funktionen, die Fehlermeldungen nicht direkt melden, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> dürfen die Methode `HRESULT`nur aufrufen, wenn sie einen Fehler zurückgeben. Es ist zulässig, `ErrorInfo` die auf dem Eintrag <xref:Microsoft.VisualStudio.VSConstants.S_OK>zu einer Funktion oder bei der Rückkehr zu löschen. Die einzige Ausnahme von dieser Regel ist, wenn ein Aufruf einen Fehler `HRESULT` zurückgibt, von dem die empfangende Partei explizit wiederherstellen oder sicher ignorieren kann.

- Jede Partei, die einen `HRESULT` Fehler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> explizit <xref:Microsoft.VisualStudio.VSConstants.S_OK>ignoriert, muss die Methode mit aufrufen. Andernfalls kann `ErrorInfo` das Objekt versehentlich verwendet werden, wenn eine `ErrorInfo`andere Partei einen Fehler generiert, ohne eine eigene bereitzustellen.

- Alle Methoden, die `HRESULT` einen Fehler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> auslösen, werden empfohlen, die Methode aufzurufen, um umfangreiche Fehlerinformationen bereitzustellen. Wenn es `HRESULT` sich `FACILITY_ITF` bei der zurückgegebenen Datei um `ErrorInfo`einen speziellen Fehler handelt, ist die Methode erforderlich, um ein richtiges Objekt bereitzustellen. Wenn es sich bei dem zurückgegebenen <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>Fehler <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>um <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>einen Standardsystemfehler handelt (z. B. , <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> , , , usw.), ist es akzeptabel, den Fehlercode zurückzugeben, ohne die Methode explizit aufzurufen. `HRESULT` Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode beim Ursprung eines Fehlers (einschließlich Systemfehlern) als defensive Codierungsstrategie auf, entweder mit `ErrorInfo` einer detaillierteren Beschreibung des Fehlers oder `null`.

- Alle Funktionen, die einen Fehler zurückgeben, der von einem anderen Aufruf `HRESULT` verursacht wurde, `ErrorInfo` müssen die Informationen weitergeben, die vom fehlerhaften Aufruf im empfangen wurden, ohne das Objekt zu ändern.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Komponentenautomatisierung)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
