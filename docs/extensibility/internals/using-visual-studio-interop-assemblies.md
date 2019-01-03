---
title: Mithilfe von Visual Studio-Interopassemblys | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b525602e5f328fefde5e552c9c99a845f369a81a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869885"
---
# <a name="using-visual-studio-interop-assemblies"></a>Verwenden von Visual Studio-Interop-Assemblys
Visual Studio-interop-Assemblys können die COM-Schnittstellen zugegriffen wird, die Bereitstellen von Visual Studio-Erweiterbarkeit, von verwaltete Anwendungen. Es gibt einige Unterschiede zwischen COM-Schnittstellen, die gerade und die Interop-Versionen. Z. B. HRESULTs sind in der Regel als Int-Werte dargestellt und in die gleiche Weise wie Ausnahmen behandelt werden müssen, und Parameter (insbesondere out-Parameter) werden unterschiedlich behandelt.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Behandeln von HRESULTs, die von COM an verwalteten Code zurückgegeben werden  
 Wenn Sie eine COM-Schnittstelle in verwaltetem Code aufrufen, überprüfen Sie den HRESULT-Wert, und lösen Sie ggf. eine Ausnahme aus. Die <xref:Microsoft.VisualStudio.ErrorHandler>-Klasse enthält die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>-Methode, die abhängig vom Wert des an sie übergebenen HRESULTs eine COM-Ausnahme auslöst.  
  
 Die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>-Methode löst standardmäßig eine Ausnahme aus, wenn ihr ein HRESULT mit einem Wert kleiner als 0 (null) übergeben wird. In Fällen, in denen solche HRESULTs zulässige Werte aufweisen und keine Ausnahme ausgelöst werden soll, müssen die Werte der zusätzlichen HRESULTS nach dem Überprüfen der Werte an <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> übergeben werden. Wenn das überprüfte HRESULT explizit an <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> übergebenen HRESULT-Werten entspricht, wird keine Ausnahme ausgelöst.  
  
> [!NOTE]
>  Die <xref:Microsoft.VisualStudio.VSConstants> -Klasse enthält Konstanten für allgemeine HRESULTS, z. B. <xref:Microsoft.VisualStudio.VSConstants.S_OK> und <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTs vorzusehen, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> und <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> enthält auch die Methoden <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> und <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, die den Makros SUCCEEDED und FAILED in COM entsprechen.  
  
 Betrachten Sie beispielsweise den folgenden Funktionsaufruf, bei dem <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> ein zulässiger Rückgabewert ist, aber alle anderen HRESULTs kleiner als 0 (null) einen Fehler darstellen.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Wenn es mehrere zulässige Rückgabewerte gibt, können zusätzliche HRESULT-Werte einfach an die Liste in dem Aufruf von <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> angefügt werden.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Von verwaltetem Code an COM zurückgegebene HRESULTS  
 Wenn keine Ausnahme auftritt, gibt der verwaltete Code <xref:Microsoft.VisualStudio.VSConstants.S_OK> an die aufrufende COM-Funktion zurück. COM-Interop unterstützt allgemeine Ausnahmen, die in verwaltetem Code stark typisiert sind. Eine Methode, die ein unzulässiges `null`-Argument empfängt, löst beispielsweise eine <xref:System.ArgumentNullException> aus.  
  
 Wenn Sie nicht sicher sind, welche Ausnahme ausgelöst werden soll, aber das HRESULT kennen, das an COM zurückgegeben werden soll, können Sie die <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>-Methode verwenden, um eine entsprechende Ausnahme auszulösen. Dies funktioniert auch bei einem nicht standardmäßigen Fehler, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> versucht, das übergebene HRESULT einer stark typisierten Ausnahme zuzuordnen. Wenn dies nicht möglich ist, wird stattdessen eine generische COM-Ausnahme ausgelöst. Als endgültiges Ergebnis wird das an <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> übergebene HRESULT vom verwaltetem Code an die aufrufende COM-Funktion zurückgegeben.  
  
> [!NOTE]
>  Ausnahmen beeinträchtigen die Leistung und dienen als Hinweis auf anormale Programmbedingungen. Häufig auftretende Bedingungen sollten inline behandelt werden, statt eine Ausnahme auszulösen.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown-Parameter übergeben wird, als Typ "void" **  
 Suchen Sie nach [out]-Parameter, die als Typ definiert sind `void **` in der COM+-Schnittstelle, aber das sind definiert als `[``iid_is``]` in die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Methodenprototyps der interop-Assembly.  
  
 In manchen Fällen eine COM-Schnittstelle generiert eine `IUnknown` Objekt und der COM-Schnittstelle anschließend übergibt es als Typ `void **`. Diese Schnittstellen sind besonders wichtig, da, wenn die Variable, als definiert ist [out] ein, in der IDL-Datei, und klicken Sie dann die `IUnknown` Objekt ist mit verweiszählung der `AddRef` Methode. Ein Arbeitsspeicherverlust tritt auf, wenn das Objekt nicht ordnungsgemäß behandelt wird.  
  
> [!NOTE]
>  Ein `IUnknown` durch die COM-Schnittstelle erstellt wird und in einer Variablen [Out] zurückgegeben bewirkt, dass einen Speicherverlust, wenn sie nicht explizit freigegeben wird.  
  
 Verwaltete Methoden, die die Behandlung solcher Objekte behandeln <xref:System.IntPtr> als Zeiger auf ein `IUnknown` Objekt aus, und rufen Sie die <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Methode, um das Objekt abzurufen. Der Aufrufer sollte dann den Rückgabewert in den Datentyp geeignet ist umgewandelt. Wenn das Objekt nicht mehr benötigt wird, rufen Sie <xref:System.Runtime.InteropServices.Marshal.Release%2A> , diese freizugeben.  
  
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
>  Die folgenden Methoden sind bekannte übergeben `IUnknown` Zeiger-Objekt als Typ <xref:System.IntPtr>. Verarbeiten Sie diese Option aus, wie in diesem Abschnitt beschrieben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out]-Parameter optional.  
 Suchen Sie nach Parametern, die als [Out] definiert werden-Datentyp (`int`, `object`usw.) in der COM+-Schnittstelle, aber das sind definiert als Arrays des gleichen Datentyps in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Methodenprototyps der interop-Assembly.  
  
 Einige COM-Schnittstellen, wie z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, [out]-Parameter als optional behandelt. Wenn ein Objekt nicht erforderlich ist, wird diese COM-Schnittstellen zurückgeben einer `null` Zeiger als Wert für diesen Parameter anstelle der [Out] Objekt erstellt. Dieser Fehler ist entwurfsbedingt. Für diese Schnittstellen `null` Zeiger wird angenommen, dass im Rahmen des VSPackage das richtige Verhalten und keine Fehlermeldung zurückgegeben.  
  
 Da die CLR nicht den Wert der [Out]-Parameter sein zulässt `null`, Teil des Verhalten dieser Schnittstellen ist nicht in verwaltetem Code direkt verfügbar sind. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop-Assembly-Methoden für die betroffenen Schnittstellen umgehen das Problem, indem Sie die relevanten Parameter als Arrays definieren, da die CLR, die Übergabe von ermöglicht `null` Arrays.  
  
 Platzieren Sie verwaltete Implementierungen dieser Methoden eine `null` Array an den Parameter, wenn nichts zurückgegeben werden. Andernfalls erstellen Sie ein Array mit einem Element mit dem richtigen Typ und den zurückgegeben Wert im Array platziert.  
  
 Verwaltete Methoden, die über Schnittstellen mit optionalen [Out] Informationen über Parameter empfängt den Parameter als ein Array. Untersuchen Sie einfach den Wert des ersten Elements des Arrays. Ist dies nicht `null`, behandeln Sie das erste Element aus, als handele es sich um den ursprünglichen Parameter.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Übergeben von Konstanten in Zeigerparameter  
 Suchen Sie nach Parametern, die als [in] Zeiger auf die COM-Schnittstelle definiert sind, aber als definiert sind, eine <xref:System.IntPtr> Geben Sie in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Methodenprototyps der interop-Assembly.  
  
 Ein ähnliches Problem tritt auf, wenn eine COM-Schnittstelle einen speziellen Wert, z. B. 0,-1 oder-2 zu, anstatt einen Objektzeiger übergibt. Im Gegensatz zu [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], die CLR lässt keine Konstanten als Objekte umgewandelt werden. Stattdessen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop-Assembly definiert den Parameter als ein <xref:System.IntPtr> Typ.  
  
 Verwaltete Implementierungen dieser Methoden sollten den Umstand nutzen, die die <xref:System.IntPtr> -Klasse verfügt über beide `int` und `void *` von Konstruktoren zum Erstellen einer <xref:System.IntPtr> über ein Objekt oder eine ganzzahlige Konstante, je nach Bedarf.  
  
 Verwaltete Methoden, die empfangen <xref:System.IntPtr> Parameter dieses Typs verwenden, sollten die <xref:System.IntPtr> geben Konvertierungsoperatoren, um die Ergebnisse zu verarbeiten. Konvertieren Sie zuerst die <xref:System.IntPtr> zu `int` und relevante ganzzahlige Konstanten getestet. Wenn keine Werte zusammenpassen, konvertieren Sie ihn in ein Objekt des erforderlichen Typs und fortfahren.  
  
 Beispiele hierfür finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE zurückgegeben Werte übergeben als [out]-Parameter  
 Suchen Sie nach Methoden, die eine `retval` Rückgabewert in der COM-Schnittstelle, aber das ein `int` Rückgabewert und ein zusätzliches [out] Arrayparameter in die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Methodenprototyps der interop-Assembly. Es muss klar, dass diese Methoden besondere Behandlung erfordern, da die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop-Assembly-Methodenprototypen haben einen weiteren Parameter als die COM-Schnittstellenmethoden.  
  
 Viele COM-Schnittstellen, die OLE-Aktivität behandeln senden Informationen über OLE-Status zurück an das aufrufende Programm, die in gespeicherten der `retval` Wert der Schnittstelle zurück. Anstatt einen Rückgabewert der entsprechenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop-Assembly-Methoden senden Sie die Informationen an das aufrufende Programm in einen [Out] gespeicherten Arrayparameter.  
  
 Verwaltete Implementierungen dieser Methoden erstellen ein Array mit einzelnen Elementen des gleichen Typs als [Out]-Parameter und fügen Sie ihn in den-Parameter. Der Wert des Arrayelements muss identisch mit den entsprechenden COM `retval`.  
  
 Verwaltete Methoden, die Schnittstellen dieses Typs aufrufen sollten das erste Element aus dem [Out] Array extrahieren. Dieses Element behandelt werden kann, als wäre er ein `retval` Wert aus der entsprechenden COM-Schnittstelle zurückzugeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)