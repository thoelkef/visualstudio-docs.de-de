---
title: Verwenden von Visual Studio Interop-Assemblys | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704137"
---
# <a name="using-visual-studio-interop-assemblies"></a>Verwenden von Visual Studio-Interop-Assemblys
Visual Studio-Interopassemblys ermöglichen verwalteten Anwendungen den Zugriff auf die COM-Schnittstellen, die Visual Studio-Erweiterbarkeit bieten. Es gibt einige Unterschiede zwischen geraden COM-Schnittstellen und deren Interop-Versionen. HRESULTs werden z. B. im Allgemeinen als int-Werte dargestellt und müssen auf die gleiche Weise wie Ausnahmen behandelt werden, und Parameter (insbesondere Out-Parameter) werden unterschiedlich behandelt.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Behandeln von HRESULTs, die von COM an verwalteten Code zurückgegeben werden
 Wenn Sie eine COM-Schnittstelle in verwaltetem Code aufrufen, überprüfen Sie den HRESULT-Wert, und lösen Sie ggf. eine Ausnahme aus. Die <xref:Microsoft.VisualStudio.ErrorHandler>-Klasse enthält die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>-Methode, die abhängig vom Wert des an sie übergebenen HRESULTs eine COM-Ausnahme auslöst.

 Die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>-Methode löst standardmäßig eine Ausnahme aus, wenn ihr ein HRESULT mit einem Wert kleiner als 0 (null) übergeben wird. In Fällen, in denen solche HRESULTs zulässige Werte aufweisen und keine Ausnahme ausgelöst werden soll, müssen die Werte der zusätzlichen HRESULTS nach dem Überprüfen der Werte an <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> übergeben werden. Wenn das überprüfte HRESULT explizit an <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> übergebenen HRESULT-Werten entspricht, wird keine Ausnahme ausgelöst.

> [!NOTE]
> Die <xref:Microsoft.VisualStudio.VSConstants> Klasse enthält konstanten für allgemeine <xref:Microsoft.VisualStudio.VSConstants.S_OK> HRESULTS, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>und <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, und HRESULTS, z. B. und . <xref:Microsoft.VisualStudio.VSConstants> enthält auch die Methoden <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> und <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, die den Makros SUCCEEDED und FAILED in COM entsprechen.

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
> Ausnahmen beeinträchtigen die Leistung und dienen als Hinweis auf anormale Programmbedingungen. Häufig auftretende Bedingungen sollten inline behandelt werden, statt eine Ausnahme auszulösen.

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown-Parameter als Typ void** übergeben
 Suchen Sie nach [out]-Parametern, die in der COM-Schnittstelle als Typ `void **` definiert sind, aber wie `[``iid_is``]` im Prototyp der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assemblymethode definiert sind.

 Manchmal generiert eine COM-Schnittstelle ein `IUnknown` Objekt, und die `void **`COM-Schnittstelle übergibt es dann als Typ . Diese Schnittstellen sind besonders wichtig, da, wenn die Variable in der `IUnknown` IDL als [out] definiert ist, das Objekt mit der `AddRef` Methode gezählt wird. Ein Speicherverlust tritt auf, wenn das Objekt nicht ordnungsgemäß behandelt wird.

> [!NOTE]
> Ein `IUnknown` Objekt, das von der COM-Schnittstelle erstellt und in einer [out]-Variablen zurückgegeben wird, verursacht einen Speicherverlust, wenn es nicht explizit freigegeben wird.

 Verwaltete Methoden, die <xref:System.IntPtr> solche Objekte behandeln, `IUnknown` sollten als <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Zeiger auf ein Objekt behandelt werden und die Methode zum Abrufen des Objekts aufrufen. Der Aufrufer sollte dann den Rückgabewert in den typ "geeignet" umwerfen. Wenn das Objekt nicht mehr <xref:System.Runtime.InteropServices.Marshal.Release%2A> benötigt wird, rufen Sie es auf, um es freizugeben.

 Im Folgenden finden Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> ein Beispiel `IUnknown` für das Aufrufen der Methode und die korrekte Behandlung des Objekts:

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
> Die folgenden Methoden sind `IUnknown` bekannt, objektzeiger <xref:System.IntPtr>als typ zu übergeben. Behandeln Sie sie wie in diesem Abschnitt beschrieben.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Optionale [out] Parameter
 Suchen Sie in der COM-Schnittstelle nach`int`Parametern, die als [out]-Datentyp ( , `object`, usw.) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] definiert sind, die jedoch als Arrays desselben Datentyps im Interop-Assembly-Methodenprototyp definiert sind.

 Einige COM-Schnittstellen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>z. B. , behandeln [out]-Parameter als optional. Wenn ein Objekt nicht erforderlich ist, `null` geben diese COM-Schnittstellen einen Zeiger als Wert dieses Parameters zurück, anstatt das [out]-Objekt zu erstellen. Dies ist beabsichtigt. Bei diesen Schnittstellen `null` werden Zeiger als Teil des korrekten Verhaltens des VSPackage angenommen, und es wird kein Fehler zurückgegeben.

 Da die CLR nicht zulässt, dass der `null`Wert eines [out]-Parameters ist, ist ein Teil des entworfenen Verhaltens dieser Schnittstellen nicht direkt innerhalb des verwalteten Codes verfügbar. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assemblymethoden für betroffene Schnittstellen umgehen das Problem, indem sie die relevanten `null` Parameter als Arrays definieren, da die CLR die Übergabe von Arrays zulässt.

 Verwaltete Implementierungen dieser Methoden `null` sollten ein Array in den Parameter setzen, wenn nichts zurückgegeben werden soll. Erstellen Sie andernfalls ein Ein-Element-Array des richtigen Typs, und geben Sie den Rückgabewert in das Array ein.

 Verwaltete Methoden, die Informationen von Schnittstellen mit optionalen [out]-Parametern empfangen, erhalten den Parameter als Array. Untersuchen Sie einfach den Wert des ersten Elements des Arrays. Wenn dies `null`nicht der Fall ist, behandeln Sie das erste Element wie den ursprünglichen Parameter.

## <a name="passing-constants-in-pointer-parameters"></a>Übergeben von Konstanten in Zeigerparametern
 Suchen Sie nach Parametern, die als [in]-Zeiger in der <xref:System.IntPtr> COM-Schnittstelle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] definiert sind, die jedoch als Typ im Prototyp der Interop-Assemblymethode definiert sind.

 Ein ähnliches Problem tritt auf, wenn eine COM-Schnittstelle einen speziellen Wert, z. B. 0, -1 oder -2, anstelle eines Objektzeigers übergibt. Im [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]Gegensatz zu lässt die CLR nicht zu, dass Konstanten als Objekte umgegossen werden. Stattdessen definiert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Interop-Assembly den <xref:System.IntPtr> Parameter als Typ.

 Verwaltete Implementierungen dieser Methoden sollten die <xref:System.IntPtr> Tatsache nutzen, `void *` dass die Klasse <xref:System.IntPtr> über beide `int` und Konstruktoren verfügt, um eine aus einem Objekt oder einer Ganzzahlkonstante zu erstellen.

 Verwaltete Methoden, die Parameter dieses Typs empfangen, <xref:System.IntPtr> sollten die <xref:System.IntPtr> Typkonvertierungsoperatoren verwenden, um die Ergebnisse zu verarbeiten. Konvertieren Sie <xref:System.IntPtr> `int` zuerst die in und testen Sie sie mit relevanten ganzzahligen Konstanten. Wenn keine Werte übereinstimmen, konvertieren Sie es in ein Objekt des erforderlichen Typs, und fahren Sie fort.

 Beispiele hierzu finden <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>Sie unter und .

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE-Rückgabewerte als [out]-Parameter übergeben
 Suchen Sie nach `retval` Methoden, die einen Rückgabewert in `int` der COM-Schnittstelle haben, aber [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einen Rückgabewert und einen zusätzlichen [out]-Arrayparameter im Interop-Assemblymethodenprototyp haben. Es sollte klar sein, dass diese [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Methoden eine spezielle Handhabung erfordern, da die Prototypen der Interop-Baugruppenmethode einen Parameter mehr als die COM-Schnittstellenmethoden aufweisen.

 Viele COM-Schnittstellen, die sich mit DER OLE-Aktivität befassen, `retval` senden Informationen über den OLE-Status zurück an das aufrufende Programm, das im Rückgabewert der Schnittstelle gespeichert ist. Anstatt einen Rückgabewert zu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwenden, senden die entsprechenden Interop-Assemblymethoden die Informationen an das aufrufende Programm zurück, das in einem [out]-Array-Parameter gespeichert ist.

 Verwaltete Implementierungen dieser Methoden sollten ein Einzelne-Element-Array desselben Typs wie der Parameter [out] erstellen und in den Parameter einteilen. Der Wert des Arrayelements sollte mit dem `retval`entsprechenden COM identisch sein.

 Verwaltete Methoden, die Schnittstellen dieses Typs aufrufen, sollten das erste Element aus dem Array [out] abrufen. Dieses Element kann so behandelt `retval` werden, als wäre es ein Rückgabewert von der entsprechenden COM-Schnittstelle.

## <a name="see-also"></a>Weitere Informationen
- [Interoperation mit nicht verwaltetem Code](/dotnet/framework/interop/index)
