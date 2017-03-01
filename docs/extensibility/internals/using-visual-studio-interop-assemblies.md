---
title: Mithilfe von Interop-Assemblys von Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 9762ba0404e739c167cadc3e9d3106c7f3ee14e8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>Mithilfe von Interop-Assemblys von Visual Studio
Visual Studio-Interop-Assemblys können verwaltete Clientanwendungen auf die COM-Schnittstellen zugreifen, die Visual Studio-Erweiterbarkeit zu ermöglichen. Es gibt einige Unterschiede zwischen COM-Schnittstellen, die gerade und die Interop-Versionen. Beispielsweise HRESULTs sind im Allgemeinen als Int-Werte dargestellt und müssen auf die gleiche Weise wie Ausnahmen behandelt werden, und Parameter (insbesondere out-Parameter) werden unterschiedlich behandelt.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Behandeln von HRESULTs, die von COM an verwalteten Code zurückgegeben werden  
 Wenn Sie eine COM-Schnittstelle in verwaltetem Code aufrufen, überprüfen Sie den HRESULT-Wert, und lösen Sie ggf. eine Ausnahme aus. Die <xref:Microsoft.VisualStudio.ErrorHandler>Klasse enthält die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>Methode, die eine COM-Ausnahme, abhängig vom Wert von HRESULT übergeben werden auslöst.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> </xref:Microsoft.VisualStudio.ErrorHandler>  
  
 In der Standardeinstellung <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>löst eine Ausnahme aus, wenn sie ein HRESULT übergeben wird, die einen Wert kleiner als&0; (null) aufweist.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> In Fällen, in denen solche HRESULTs sind die zulässigen Werte und keine Ausnahme ausgelöst werden soll, die Werte der zusätzlichen HRESULTS an übergeben werden sollte <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>nach die Werten getestet werden.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Wenn HRESULT getesteten HRESULT Werte explizit übergeben entspricht <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, wird keine Ausnahme ausgelöst.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
> [!NOTE]
>  Die <xref:Microsoft.VisualStudio.VSConstants>-Klasse enthält Konstanten für allgemeine HRESULTS, z. B. <xref:Microsoft.VisualStudio.VSConstants.S_OK>und <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>und <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> </xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> </xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> </xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants>enthält zudem die <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>und <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>die entsprechen den Erfolg und Fehler Makros in COM-Methoden</xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> </xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A></xref:Microsoft.VisualStudio.VSConstants>  
  
 Betrachten Sie beispielsweise den folgenden Funktionsaufruf in der <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>eine akzeptable Rückgabewert, aber alle anderen HRESULT ist kleiner als&0; (null) stellt einen Fehler.</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>  
  
 [!code-vb[VSSDKHRESULTInformation&#1;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] 
 [!code-cs [VSSDKHRESULTInformation Nr.&1;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Wenn es mehr als eine akzeptable Werte zurückgeben, können zusätzliche HRESULT-Werte nur im Aufruf von <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> angefügt werden  
  
 [!code-vb[VSSDKHRESULTInformation&2;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] 
 [!code-cs [VSSDKHRESULTInformation Nr.&2;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Von verwaltetem Code an COM zurückgegebene HRESULTS  
 Wenn keine Ausnahme auftritt, gibt verwalteter Code <xref:Microsoft.VisualStudio.VSConstants.S_OK>, der COM-Funktion, die it.</xref:Microsoft.VisualStudio.VSConstants.S_OK> COM-Interop unterstützt allgemeine Ausnahmen, die in verwaltetem Code stark typisiert sind. Angenommen, eine Methode, die eine unzulässige empfängt `null` Argument löst eine <xref:System.ArgumentNullException>.</xref:System.ArgumentNullException>  
  
 Wenn Sie nicht sicher welche Ausnahme sind ausgelöst werden, aber Sie wissen, dass das HRESULT zurückgegeben werden soll, COM, können Sie die <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>Methode, um eine entsprechende Ausnahme ausgelöst.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Dies funktioniert auch mit einer nicht dem Standard entsprechende Fehler, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>Versuche, ordnen Sie das HRESULT übergeben, in eine stark typisierte Ausnahme.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Wenn dies nicht möglich ist, wird stattdessen eine generische COM-Ausnahme ausgelöst. Das endgültige Ergebnis ist, dass Sie das HRESULT <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>von verwaltetem Code</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> zurückgegeben, der COM-Funktion, die it. übergeben  
  
> [!NOTE]
>  Ausnahmen beeinträchtigen die Leistung und dienen als Hinweis auf anormale Programmbedingungen. Häufig auftretende Bedingungen sollten inline behandelt werden, statt eine Ausnahme auszulösen.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown-Parameter übergeben, als Typ Void **  
 Suchen Sie nach [out]-Parameter, die als Typ definiert werden `void **` in der COM-Schnittstelle, die jedoch als definiert sind `[``iid_is``]` in den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prototyp der Interop-Assembly-Methode.  
  
 Eine COM-Schnittstelle in manchen Fällen generiert ein `IUnknown` Objekt und der COM-Schnittstelle gibt es als Typ `void **`. Diese Schnittstellen sind besonders wichtig, da, wenn die Variable als definiert ist [out], in der IDL-Datei, die `IUnknown` -Objekt ist mit referenzzählung der `AddRef` Methode. Wenn das Objekt nicht ordnungsgemäß behandelt wird, tritt ein Speicherverlust auf.  
  
> [!NOTE]
>  Ein `IUnknown` Objekt durch die COM-Schnittstelle erstellt und zurückgegeben, die in einer Variablen [Out] bewirkt, dass einen Speicherverlust wird nicht explizit freigegeben.  
  
 Verwaltete Methoden, die solche Objekte behandeln sollten behandeln <xref:System.IntPtr>als Zeiger auf eine `IUnknown` -Objekt, und rufen Sie die <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>Methode, um das Objekt abzurufen.</xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> </xref:System.IntPtr> Der Aufrufer sollte dann umgewandelt, den Rückgabewert gleich welcher Art geeignet ist. Wenn das Objekt nicht mehr benötigt wird, rufen Sie auf, <xref:System.Runtime.InteropServices.Marshal.Release%2A>um es loslassen</xref:System.Runtime.InteropServices.Marshal.Release%2A>  
  
 Folgt ein Beispiel eines Aufrufs der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>-Methode und die Behandlung der `IUnknown` Objekt ordnungsgemäß:</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
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
>  Die folgenden Methoden sind bekanntermaßen übergeben `IUnknown` Zeiger als Typ <xref:System.IntPtr>.</xref:System.IntPtr> -Objekt Verarbeiten Sie diese Option aus, wie in diesem Abschnitt beschrieben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out]-Parameter optional.  
 Suchen Sie nach Parametern, die als [Out] definiert sind-Datentyp (`int`, `object`usw.) in der COM-Schnittstelle, die jedoch werden definiert als Arrays des gleichen Datentyps in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prototyp der Interop-Assembly-Methode.  
  
 Einige COM-Schnittstellen, wie z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, [out]-Parameter als optional zu behandeln.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> Wenn ein Objekt nicht erforderlich ist, diese COM-Schnittstellen zurückgeben einer `null` Zeiger als Wert für diesen Parameter anstelle der [Out]-Objekt erstellen. Dieser Fehler ist entwurfsbedingt. Für diese Schnittstellen `null` Zeiger wird angenommen, dass im Rahmen des VSPackage das korrekte Verhalten und kein Fehler zurückgegeben.  
  
 Da die CLR nicht den Wert der ein [Out]-Parameter werden zulässt `null`, Teil des Verhalten dieser Schnittstellen ist nicht direkt innerhalb von verwaltetem Code verfügbar sind. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assembly-Methoden für die betroffenen Schnittstellen umgehen das Problem, indem die relevanten Parameter als Arrays definieren, da die CLR ermöglicht die Übergabe von es `null` Arrays.  
  
 Verwaltete Implementierungen dieser Methoden sollten eine `null` Array an den Parameter, wenn nichts zurückgegeben werden. Andernfalls erstellen Sie ein Array einem Element mit dem richtigen Typ und eingefügten Sie den Rückgabewert in das Array.  
  
 Verwaltete Methoden, die über Schnittstellen mit optionalen [Out] Informationen über Parameter empfängt den Parameter als ein Array. Überprüfen Sie einfach den Wert des ersten Elements des Arrays. Ist dies nicht `null`, das erste Element zu behandeln, als handele es sich um den ursprünglichen Parameter.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Übergeben von Konstanten in Zeigerparameter  
 Suchen Sie nach Parameter als [in] Zeiger in der COM-Schnittstelle definiert sind, jedoch als definiert sind ein <xref:System.IntPtr>Geben Sie in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assembly Methode Prototyp.</xref:System.IntPtr>  
  
 Ein ähnliches Problem tritt auf, wenn eine COM-Schnittstelle einen speziellen Wert, z. B. 0, 1 oder – 2, statt einen Objektzeiger übergibt. Im Gegensatz zu [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], die CLR lässt keine Konstanten in Objekte umgewandelt werden. In diesem Fall die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assembly definiert den Parameter als einen <xref:System.IntPtr>Typ.</xref:System.IntPtr>  
  
 Verwaltete Implementierungen dieser Methoden sollten den Umstand nutzen, die die <xref:System.IntPtr>-Klasse verfügt über beide `int` und `void *` Konstruktoren erstellen ein <xref:System.IntPtr>je nach Bedarf entweder ein Objekt oder eine ganzzahlige Konstante,.</xref:System.IntPtr> </xref:System.IntPtr>  
  
 Verwaltete Methoden, die empfangen <xref:System.IntPtr>Parameter dieses Typs verwenden, sollte die <xref:System.IntPtr>Geben Konvertierungsoperatoren, um die Ergebnisse zu verarbeiten.</xref:System.IntPtr> </xref:System.IntPtr> Konvertieren Sie zuerst die <xref:System.IntPtr>, `int` und testen es anhand der entsprechenden ganzzahligen Konstanten.</xref:System.IntPtr> Wenn keine Werte übereinstimmen, konvertieren Sie ihn in ein Objekt des erforderlichen Typs und fortfahren.  
  
 Beispiele hierzu finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE zurückgeben übergebenen Werte als [out]-Parameter  
 Suchen nach Methoden, die über eine `retval` Rückgabewert in der COM-Schnittstelle, jedoch ein `int` Rückgabewert und ein zusätzliches [out]-Array-Parameters in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prototyp der Interop-Assembly-Methode. Es sollte klar, dass diese Methoden besondere Behandlung erfordern, da die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assembly Methodenprototypen haben einen weiteren Parameter als die Methoden der COM-Schnittstelle.  
  
 Viele COM-Schnittstellen, die mit OLE-Aktivität arbeiten senden Informationen über OLE-Status zurück an das aufrufende Programm in gespeicherten der `retval` Rückgabewert der Schnittstelle. Anstelle der entsprechenden Rückgabewert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-assemblymethoden senden die Informationen zurück an das aufrufende Programm in einen [Out] gespeicherten Arrayparameter.  
  
 Verwaltete Implementierungen dieser Methoden ein Array mit einzelnen Elementen des gleichen Typs als [Out]-Parameter erstellen, und fügen Sie ihn in den-Parameter. Der Wert des Arrayelements muss identisch mit den entsprechenden COM `retval`.  
  
 Verwaltete Methoden, die Schnittstellen dieser Art sollten das erste Element aus dem [Out] Array extrahieren. Dieses Element kann behandelt werden, als wäre er ein `retval` Wert aus der entsprechenden COM-Schnittstelle zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Interoperation mit nicht verwaltetem Code](http://msdn.microsoft.com/Library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
