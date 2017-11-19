---
title: Mithilfe von Visual Studio-Interopassemblys | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 298caf0b1c65ecb3612b927859b4d7d01720fc27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="using-visual-studio-interop-assemblies"></a>Mithilfe von Visual Studio-Interopassemblys
Visual Studio-Interopassemblys können verwaltete Anwendungen auf die COM-Schnittstellen, die Visual Studio-Erweiterbarkeit bereitstellen. Es gibt einige Unterschiede zwischen COM-Schnittstellen, die gerade und die Interop-Versionen. Beispielsweise HRESULTs sind in der Regel als Int-Werte dargestellt und müssen auf die gleiche Weise wie Ausnahmen behandelt werden und Parameter (insbesondere out-Parameter) unterschiedlich behandelt.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Behandeln von HRESULTs, die von COM an verwalteten Code zurückgegeben werden  
 Wenn Sie eine COM-Schnittstelle in verwaltetem Code aufrufen, überprüfen Sie den HRESULT-Wert, und lösen Sie ggf. eine Ausnahme aus. Die <xref:Microsoft.VisualStudio.ErrorHandler> Klasse enthält die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> -Methode, die eine COM-, je nach dem Wert von HRESULT Ausnahme an sie übergeben.  
  
 Standardmäßig <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> löst eine Ausnahme aus, wenn sie ein HRESULT übergeben wird, die einen Wert kleiner als 0 (null) ist. In Fällen, in denen solche HRESULTs zulässige Werte sind und es werden keine Ausnahmen ausgelöst werden soll, die Werte der zusätzlichen HRESULTS an übergeben werden sollte <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> nach dem Überprüfen der Werte. Wenn das ÜBERPRÜFTE alle HRESULT-Werte, die explizit übergeben entspricht <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, wird keine Ausnahme ausgelöst.  
  
> [!NOTE]
>  Die <xref:Microsoft.VisualStudio.VSConstants> -Klasse enthält Konstanten für allgemeine HRESULTS, z. B. <xref:Microsoft.VisualStudio.VSConstants.S_OK> und <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> und <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants>bietet außerdem die <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> und <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> Methoden, die den Makros SUCCEEDED und FAILED in COM entsprechen  
  
 Betrachten Sie beispielsweise den folgenden Funktionsaufruf, bei dem <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> ist ein zulässiger Rückgabewert aber alle anderen HRESULTs kleiner als 0 (null) einen Fehler darstellen.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Wenn es mehrere zulässige Rückgabewerte sind, zusätzliche HRESULT-Werte können nur angefügt werden der Liste auf den Aufruf von <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Von verwaltetem Code an COM zurückgegebene HRESULTS  
 Wenn keine Ausnahme auftritt, gibt der verwaltete Code <xref:Microsoft.VisualStudio.VSConstants.S_OK> an COM-Funktion, die diese aufgerufen. COM-Interop unterstützt allgemeine Ausnahmen, die in verwaltetem Code stark typisiert sind. Angenommen, eine Methode, die ein unzulässiges empfängt `null` Argument löst eine <xref:System.ArgumentNullException>.  
  
 Wenn Sie nicht sicher sind welche Ausnahme ausgelöst, aber Sie wissen, dass das HRESULT zurückgegeben werden soll, COM, können Sie die <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Methode, um eine entsprechende Ausnahme auszulösen. Dies funktioniert auch bei einem nicht standardmäßigen Fehler, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>versucht, ordnen Sie das HRESULT, die in eine stark typisierte Ausnahme an es übergeben werden. Wenn dies nicht möglich ist, wird stattdessen eine generische COM-Ausnahme ausgelöst. Das endgültige Ergebnis ist, dass das HRESULT an Sie übergeben <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> aus verwaltetem Code wird zurückgegeben, die COM-Funktion, die diese aufgerufen.  
  
> [!NOTE]
>  Ausnahmen beeinträchtigen die Leistung und dienen als Hinweis auf anormale Programmbedingungen. Häufig auftretende Bedingungen sollten inline behandelt werden, statt eine Ausnahme auszulösen.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown-Parameter übergeben, als Typ "void" **  
 [Out]-Parameter an, die als Typ definiert werden gesucht `void **` in der COM-Schnittstelle, die jedoch als definiert sind `[``iid_is``]` in die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prototyp der Interop-Assembly-Methode.  
  
 Eine COM-Schnittstelle in manchen Fällen generiert ein `IUnknown` Objekt und der COM-Schnittstelle übergibt diese als Typ `void **`. Diese Schnittstellen sind besonders wichtig, da, wenn die Variable, als definiert ist [out] ein, in der IDL-Datei und dann die `IUnknown` Objekt ist mit verweiszählung die `AddRef` Methode. Wenn das Objekt nicht ordnungsgemäß behandelt wird, tritt ein Speicherverlust auf.  
  
> [!NOTE]
>  Ein `IUnknown` Objekt von der COM-Schnittstelle erstellt und zurückgegeben, die in einer Variablen [Out] bewirkt, dass einen Speicherverlust nicht explizit freigegeben wird.  
  
 Verwaltete Methoden, die solche Objekte behandeln sollten behandeln <xref:System.IntPtr> als Zeiger auf eine `IUnknown` -Objekt, und rufen Sie die <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Methode, um das Objekt abzurufen. Der Aufrufer sollte dann umgewandelt, den Rückgabewert in der Typ geeignet ist. Wenn das Objekt nicht mehr benötigt wird, rufen Sie <xref:System.Runtime.InteropServices.Marshal.Release%2A> , diese freizugeben.  
  
 Folgt ein Beispiel eines Aufrufs der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> -Methode und die Behandlung der `IUnknown` Objekt ordnungsgemäß:  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  Die folgenden Methoden ist bekannt, dass übergeben `IUnknown` Zeiger-Objekt als Typ <xref:System.IntPtr>. Verarbeiten Sie diese Option aus, wie in diesem Abschnitt beschrieben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out]-Parameter optional.  
 Suchen Sie nach Parametern, die als [Out] definiert sind-Datentyp (`int`, `object`usw.) in der COM-Schnittstelle, die jedoch als Arrays des gleichen Datentyps in definiert werden die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prototyp der Interop-Assembly-Methode.  
  
 Einige COM-Schnittstellen, wie z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, [out]-Parameter als optional zu behandeln. Wenn ein Objekt nicht erforderlich ist, diese COM-Schnittstellen zurückgeben einer `null` Zeiger als Wert dieses Parameters anstelle der [Out] Objekt erstellen. Dieser Fehler ist entwurfsbedingt. Diese Schnittstellen `null` Zeiger wird angenommen, dass als Teil des VSPackage das richtige Verhalten und wird kein Fehler zurückgegeben.  
  
 Da die CLR nicht den Wert, der ein [Out]-Parameter werden zulässt `null`, Teil des Verhalten dieser Schnittstellen ist nicht direkt in verwaltetem Code zur Verfügung. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assembly-Methoden für die betroffenen Schnittstellen umgehen das Problem, indem Sie die relevanten Parameter als Arrays definieren, da die CLR die Übergabe von ermöglicht `null` Arrays.  
  
 Um verwaltete Implementierungen dieser Methoden sollten eine `null` Array, in den Parameter, wenn es ist nichts zum zurückgegeben werden. Andernfalls erstellen Sie ein Array mit Elementen einer mit dem richtigen Typ und eingefügten Sie den Rückgabewert in das Array.  
  
 Verwaltete Methoden, die von Schnittstellen, mit optionalen [Out] Informationen über Parameter empfängt den Parameter als Array. Überprüfen Sie nur den Wert des ersten Elements des Arrays. Ist er nicht `null`, das erste Element zu behandeln, als handele es sich um den ursprünglichen Parameter.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Übergeben von Konstanten in Zeigerparameter  
 Suchen Sie nach Parametern wie [in] Zeiger in der COM-Schnittstelle definiert sind, aber als definiert sind eine <xref:System.IntPtr> Geben Sie in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prototyp der Interop-Assembly-Methode.  
  
 Ein ähnliches Problem tritt auf, wenn eine COM-Schnittstelle einen speziellen Wert, z. B. 0,-1 oder-2 zu, anstatt ein Objektzeiger übergibt. Im Gegensatz zu [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], die CLR lässt sich nicht auf die Konstanten, mit denen Objekte umgewandelt werden. Stattdessen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assembly definiert den Parameter als ein <xref:System.IntPtr> Typ.  
  
 Um verwaltete Implementierungen dieser Methoden sollten den Umstand nutzen, die die <xref:System.IntPtr> -Klasse verfügt über beide `int` und `void *` Konstruktoren erstellen ein <xref:System.IntPtr> über ein Objekt oder eine ganzzahlige Konstante, entsprechend den Anforderungen.  
  
 Verwaltete Methoden, die empfangen <xref:System.IntPtr> Parameter dieses Typs zu verwendende der <xref:System.IntPtr> geben Konvertierungsoperatoren, um die Ergebnisse zu verarbeiten. Konvertieren Sie zuerst die <xref:System.IntPtr> auf `int` und Testen des Dokuments anhand der entsprechenden ganzzahligen Konstanten. Wenn keine Werte zusammenpassen, konvertieren Sie ihn in ein Objekt des erforderlichen Typs und den Vorgang fortzusetzen.  
  
 Beispiele hierzu finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE zurückgeben Werte als übergeben [out]-Parameter  
 Suchen Sie nach den Methoden, die über eine `retval` Rückgabewert in der COM-Schnittstelle, die jedoch eine `int` Rückgabewert und ein zusätzliches [out] Arrayparameter in die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prototyp der Interop-Assembly-Methode. Es sollte klar, dass diese Methoden besondere Behandlung erfordern, da die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assembly Methodenprototypen haben eine weitere Parameter als die Methoden der COM-Schnittstelle.  
  
 Viele COM-Schnittstellen, die mit OLE-Aktivität senden Sie Informationen über OLE-Status zurück an das aufrufende Programm gespeichert, der `retval` Rückgabewert der Schnittstelle. Anstatt einen Rückgabewert der entsprechenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assembly senden die Informationen an das aufrufende Programm in einen [Out] gespeichert Arrayparameter.  
  
 Um verwaltete Implementierungen dieser Methoden sollten ein Einzelelement-Array des gleichen Typs als [Out]-Parameter erstellen und speichern diese im Parameters. Der Wert des Arrayelements muss identisch mit den entsprechenden COM `retval`.  
  
 Verwaltete Methoden, die dieses Typs Schnittstellen aufzurufen, sollte das erste Element aus dem [Out] Array einziehen. Dieses Element kann behandelt werden, als wäre er eine `retval` Rückgabewert aus der entsprechenden COM-Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)