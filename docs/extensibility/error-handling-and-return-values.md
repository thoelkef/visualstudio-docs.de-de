---
title: "Fehlerbehandlung und Rückgabewerte | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3a197bb5dd12c1d8404ddf63976f9dbf4b63823
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="error-handling-and-return-values"></a>Fehlerbehandlung und Rückgabewerte
VSPackages und COM-verwenden die gleiche Architektur auf Fehler. Die `SetErrorInfo` und `GetErrorInfo` Funktionen sind Teil der Win32-Anwendungsprogrammierschnittstelle (API). Alle VSPackage in der integrierten Entwicklungsumgebung (IDE) kann diese global Win32-APIs, um ausführliche Fehlerinformationen Datensatz aufrufen, beim Empfangen einer benachrichtigungs über einen Fehler. Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Interop-Assemblys zum Verwalten von Fehlerinformationen enthält.  
  
## <a name="interop-methods"></a>Interop-Methoden  
 Zur Vereinfachung der IDE bietet eine Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, verwenden Sie anstelle der Win32-APIs aufrufen. In verwaltetem Code verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Auftreten eines Fehlers `HRESULT` geht auf die Ebene, in dem die Fehlermeldung angezeigt werden kann sollte (Dies ist häufig das Objekt implementieren eine <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Befehlshandler), die IDE verwendet eine andere Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, um das entsprechende Meldungsfeld anzuzeigen. In verwaltetem Code verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methode.  
  
 Als eine VSPackage-Implementierung, die COM-Objekte normalerweise implementieren `ISupportErrorInfo`. Die `ISupportErrorInfo` Schnittstelle stellt sicher, dass ausführliche Fehlerinformationen der Aufrufkette vertikal verschoben werden kann. Objekte, die über die Prozesse oder Threads verwendet werden können müssen unterstützen `ISupportErrorInfo` um sicherzustellen, dass die ausführliche Fehlerinformationen ordnungsgemäß an den Aufrufer gemarshallt wird.  
  
 Alle Objekte, beziehen sich auf VSPackages und Erweitern der IDE, einschließlich editorfactorys, Editoren, Hierarchien, beteiligt und Dienste angeboten werden, sollten ausführliche Fehlerinformationen unterstützen. Während die IDE nicht diese VSPackage-Objekte implementieren erfordert `ISupportErrorInfo`, es wird immer empfohlen.  
  
 Die IDE ist verantwortlich für Fehlerinformationen reporting und Anzeige für Benutzer einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] immer ein `HRESULT` der IDE weitergegeben wird. Die IDE ist auch der Mechanismus zum Erstellen von `ErrorInfo` Objekte.  
  
## <a name="general-guidelines"></a>Allgemeine Richtlinien  
 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methoden zum Festlegen und Fehlermeldungen angezeigt werden, die für Ihr VSPackage-Implementierung intern sind. Allerdings als allgemeine Regel, führen Sie folgende Hinweise für die Verarbeitung von Fehlermeldungen in Ihrem VSPackage:  
  
-   Implementieren `ISupportErrorInfo` in den VSPackage-COM-Objekten.  
  
-   Erstellen Sie einen fehlerberichterstellungs-Mechanismus, der Aufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode in Objekte, die implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Lassen Sie die IDE Fehler anzuzeigen, die für Benutzer über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methode.  
  
## <a name="error-information-in-the-ide"></a>Fehlerinformationen in der IDE  
 Die folgenden Regeln anzugeben, wie Fehlerinformationen im behandelt die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Wie eine defensive Strategie, um sicherzustellen, dass veraltete Fehlerinformationen nicht an Benutzer übertragen, gemeldet wird, funktioniert dieser Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> -Methodenaufruf sollte zuerst die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode. Übergeben Sie `null` zwischengespeicherte Fehlermeldungen zu löschen, bevor Aufruf nichts, neue Fehlerinformationen festlegt.  
  
-   Funktionen, die Fehlermeldungen nicht direkt Berichten dürfen nur aufrufen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode, wenn sie einen Fehler zurückgeben `HRESULT`. Es ist zulässig, deaktivieren Sie die `ErrorInfo` auf den Eintrag für eine Funktion oder beim Zurückgeben der <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Die einzige Ausnahme dieser Regel wird beim Aufruf einen Fehler zurückgegeben `HRESULT` aus dem die empfangende Partei kann explizit wiederhergestellt oder ignorieren.  
  
-   Eine Partei, die explizit einen Fehler ignoriert `HRESULT` aufrufen, müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode mit <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Andernfalls die `ErrorInfo` Objekt möglicherweise versehentlich verwendet werden, wenn eine andere Partei einen Fehler generiert, ohne dass ihre eigenen `ErrorInfo`.  
  
-   Alle Methoden, die einen Fehler stammen `HRESULT` dialogfeldmechanismen ratsam, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode, um ausführliche Fehlerinformationen bereitzustellen. Wenn das zurückgegebene `HRESULT` ist ein spezieller `FACILITY_ITF` Fehler, und klicken Sie dann auf die Methode ist erforderlich, um eine echte bieten `ErrorInfo`Objekt. Die zurückgegebene Fehler ist ein standard Systemfehler (z. B. <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>, usw.) Es ist zulässig, die den Fehlercode zurück, ohne explizit aufzurufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode. Als defensiven Code Strategie, wenn einen Fehler mit Ursprung `HRESULT` (einschließlich Systemfehler), rufen Sie immer die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> -Methode, entweder mit `ErrorInfo` fehlerbeschreibung detaillierter oder `null`.  
  
-   Rufen Sie alle Funktionen, die ein Fehler durch einen anderen Aufruf stammt muss auf die Informationen, die von der fehlerhaften empfangen wurde übergeben zurückgeben, in der `HRESULT` ohne Änderung der `ErrorInfo` Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (Komponentenautomatisierung)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo-Schnittstelle](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)