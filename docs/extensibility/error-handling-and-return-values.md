---
title: "Fehlerbehandlung und R&#252;ckgabewerte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fehler [Visual Studio SDK] behandeln"
  - "Fehlerbehandlung"
  - "Rückgabewerte"
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Fehlerbehandlung und R&#252;ckgabewerte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages und COM\-verwenden die gleiche Architektur auf Fehler. Die `SetErrorInfo` und `GetErrorInfo` Funktionen sind Teil der Win32\-Anwendungsprogrammierschnittstelle \(API\). Jedem VSPackage in der integrated Development Environment \(IDE\) kann diese globalen Win32\-APIs, um aussagekräftige Fehlerinformationen Datensatz beim Aufrufen eine fehlerbenachrichtigung empfangen. Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet Interop\-Assemblys, um Fehlerinformationen zu verwalten.  
  
## Interop\-Methoden  
 Zur Vereinfachung der IDE bietet eine Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, anstelle der Win32\-APIs verwenden. In verwaltetem Code verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Wenn ein Fehler `HRESULT` eingeht, die auf der Ebene, in dem die Fehlermeldung angezeigt werden soll \(Dies ist häufig das Objekt implementieren ein <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Befehlshandler\), die IDE verwendet eine andere Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, um das entsprechende Meldung anzuzeigen. In verwaltetem Code verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methode.  
  
 Ausführender ein VSPackage implementieren Ihrer COM\-Objekte normalerweise `ISupportErrorInfo`. Die `ISupportErrorInfo` Schnittstelle stellt sicher, dass der Aufrufkette vertikal ausführlichen Fehlerinformationen verschieben kann. Objekte, die über die Prozesse oder Threads verwendet werden können müssen unterstützen `ISupportErrorInfo` um sicherzustellen, dass die ausführlichen Fehlerinformationen ordnungsgemäß an den Aufrufer gemarshallt wird.  
  
 Alle Objekte, die mit VSPackages verknüpft und die Beteiligten in der IDE\-Editor\-Factorys, Editoren, Hierarchien, erweitern und angebotenen Dienste, sollten aussagekräftige Fehlerinformationen unterstützt. Während die IDE diese VSPackage\-Objekte implementiert keine erfordert `ISupportErrorInfo`, es wird immer empfohlen.  
  
 Die IDE ist verantwortlich für Fehlerinformationen gemeldet werden und an den Benutzer anzeigen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] immer ein `HRESULT` an der IDE weitergegeben. Die IDE ist auch der Mechanismus zum Erstellen von `ErrorInfo` Objekte.  
  
## Allgemeine Richtlinien  
 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methoden zum Festlegen und Melden von Fehlern, die intern für die VSPackage\-Implementierung sind. Allerdings als allgemeine Regel Richtlinien Sie folgenden zur Behandlung von Fehlermeldungen in das VSPackage:  
  
-   Implementieren `ISupportErrorInfo` in den VSPackage\-COM\-Objekten.  
  
-   Erstellen Sie einen Fehlerberichtmechanismus Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> \-Methode in Objekte, die implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Lassen Sie die Fehler anzuzeigen, die für Benutzer über die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methode.  
  
## Fehlerinformationen in der IDE  
 Die folgenden Regeln anzugeben, das Durchführen von Fehlerinformationen in die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Wie eine Schutzstrategie zu garantieren, dass veraltete Fehlerinformationen für Benutzer nicht gemeldet werden Funktionen, die diesen Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methodenaufruf sollten zunächst die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode. Übergeben Sie `null` zwischengespeicherte Fehlermeldungen zu deaktivieren, bevor Aufrufen von allen Elementen, die neue Fehlerinformationen eingerichtet werden kann.  
  
-   Funktionen, die nicht direkt Fehlermeldungen Berichten dürfen nur zum Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode, wenn sie einen Fehler zurückgeben `HRESULT`. Es ist zulässig, deaktivieren Sie die `ErrorInfo` auf den Eintrag für eine Funktion oder beim Zurückgeben der <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Die einzige Ausnahme von dieser Regel wird ein Aufruf einen Fehler zurückgibt, `HRESULT` von dem die empfangende Partei kann explizit wiederherstellen oder ignorieren.  
  
-   Eine Partei, die explizit einen Fehler ignoriert `HRESULT` aufrufen, müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> \-Methode mit <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Andernfalls die `ErrorInfo` Objekt möglicherweise versehentlich verwendet werden, wenn eine andere Partei einen Fehler generiert, ohne dass ihre eigenen `ErrorInfo`.  
  
-   Alle Methoden, die einen Fehler stammen `HRESULT` wird empfohlen, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode, um umfassende Informationen bereitzustellen. Wenn das zurückgegebene `HRESULT` ist eine spezielle `FACILITY_ITF` Fehler, und klicken Sie dann auf die Methode ist erforderlich, um eine ordnungsgemäße bieten `ErrorInfo`Objekt. Die zurückgegebene Fehler ist ein standard\-Fehler \(z. B. <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>, und so weiter.\) Es ist akzeptabel, den Fehlercode zurück, ohne den expliziten Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode. Als defensive Programmierung Strategie, wenn einen Fehler mit Ursprung `HRESULT` \(einschließlich Systemfehler\), rufen Sie immer die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> \-Methode, mit der `ErrorInfo` die Fehler detaillierter beschrieben oder `null`.  
  
-   Rufen Sie alle Funktionen, die zurückgeben, ein Fehler durch einen anderen Aufruf stammt muss auf die Informationen, die den fehlerhaften erhielt übergeben, in der `HRESULT` ohne Änderung der `ErrorInfo` Objekt.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo \(Component Automation\)](http://msdn.microsoft.com/de-de/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/de-de/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo Interface](http://msdn.microsoft.com/de-de/42d33066-36b4-4a5b-aa5d-46682e560f32)