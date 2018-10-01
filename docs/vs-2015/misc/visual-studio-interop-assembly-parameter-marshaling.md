---
title: Visual Studio-Interop-Assembly-Parameter-Marshalling | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: 77b94eeb4195654edabdd566eae762593b785496
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514325"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Parameter-Marshalling für Visual Studio-Interopassemblys
VSPackages, die in verwaltetem Code geschrieben sind möglicherweise aufrufen oder von nicht verwalteten COM-Code aufgerufen werden. In der Regel Methodenargumente umgewandelt oder gemarshallt werden, automatisch von der interop-Marshaller. Allerdings können keine Argumente manchmal nicht in einer unkomplizierten Weise transformiert werden. In diesen Fällen werden die interop-Assembly-Methode Prototyp-Parameter verwendet, um die COM-Funktionsparameter so weit wie möglich entsprechen. Weitere Informationen finden Sie unter [Interop-Marshalling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Allgemeine Empfehlungen  
  
##### <a name="read-the-reference-documentation"></a>Lesen Sie die Referenzdokumentation  
 Eine effektive Methode zur Interoperabilitätsprobleme zu erkennen ist, lesen die Referenzdokumentation für die einzelnen Methoden.  
  
 Die Referenzdokumentation für jede Methode enthält drei relevanten Abschnitte:  
  
-   Die [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Prototyp der COM-Funktion.  
  
-   Der Prototyp des interop-Assembly-Methode.  
  
-   Eine Liste der COM-Parameter und eine kurze Beschreibung der einzelnen.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Suchen Sie nach den Unterschieden zwischen den zwei Prototypen  
 Die meisten Interoperabilitätsprobleme abgeleitet von Konflikten zwischen der Definition eines bestimmten Typs in eine COM-Schnittstelle und die Definition des gleichen Typs in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop-Assemblys. Betrachten Sie beispielsweise den Unterschied in der Lage, übergeben Sie einen `null` Wert in einen [Out]-Parameter. Sie müssen Unterschiede zwischen den zwei Prototypen suchen und betrachten Sie die Auswirkungen für die Daten übergeben werden.  
  
##### <a name="read-the-parameter-definitions"></a>Lesen Sie die Parameterdefinitionen  
 Lesen Sie die Parameterdefinitionen. COM ist weniger streng als die common Language Runtime (CLR) über das Kombinieren von verschiedenen Arten von Daten in einem einzelnen Parameter. Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] COM-Schnittstellen voll ausnutzen dieser Flexibilität. Alle Parameter, der erfolgreich "oder" erfordern einen nicht standardmäßigen Wert oder den Typ der Daten, z. B. einen konstanten Wert in einen Zeigerparameter, sollte daher in der Dokumentation beschrieben werden.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>IUnknown-Objekte übergeben, als Typ "void" **  
 Suchen Sie nach [out]-Parameter, die als Typ definiert sind `void **` in der COM+-Schnittstelle, aber das sind definiert als `[``iid_is``]` in die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Methodenprototyps der interop-Assembly.  
  
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
  
### <a name="optional-out-parameters"></a>[Out]-Parameter optional.  
 Suchen Sie nach Parametern, die als [Out] definiert werden-Datentyp (`int`, `object`usw.) in der COM+-Schnittstelle, aber das sind definiert als Arrays des gleichen Datentyps in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Methodenprototyps der interop-Assembly.  
  
 Einige COM-Schnittstellen, wie z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, [out]-Parameter als optional behandelt. Wenn ein Objekt nicht erforderlich ist, wird diese COM-Schnittstellen zurückgeben einer `null` Zeiger als Wert für diesen Parameter anstelle der [Out] Objekt erstellt. Dieser Fehler ist entwurfsbedingt. Für diese Schnittstellen `null` Zeiger wird angenommen, dass im Rahmen des VSPackage das richtige Verhalten und keine Fehlermeldung zurückgegeben.  
  
 Da die CLR nicht den Wert der [Out]-Parameter sein zulässt `null`, Teil des Verhalten dieser Schnittstellen ist nicht in verwaltetem Code direkt verfügbar sind. Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop-Assembly-Methoden für die betroffenen Schnittstellen umgehen das Problem, indem Sie die relevanten Parameter als Arrays definieren, da die CLR, die Übergabe von ermöglicht `null` Arrays.  
  
 Platzieren Sie verwaltete Implementierungen dieser Methoden eine `null` Array an den Parameter, wenn nichts zurückgegeben werden. Andernfalls erstellen Sie ein Array mit einem Element mit dem richtigen Typ und den zurückgegeben Wert im Array platziert.  
  
 Verwaltete Methoden, die über Schnittstellen mit optionalen [Out] Informationen über Parameter empfängt den Parameter als ein Array. Untersuchen Sie einfach den Wert des ersten Elements des Arrays. Ist dies nicht `null`, behandeln Sie das erste Element aus, als handele es sich um den ursprünglichen Parameter.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Übergeben von Konstanten in Zeigerparameter  
 Suchen Sie nach Parametern, die als [in] Zeiger auf die COM-Schnittstelle definiert sind, aber als definiert sind, eine <xref:System.IntPtr> Geben Sie in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Methodenprototyps der interop-Assembly.  
  
 Ein ähnliches Problem tritt auf, wenn eine COM-Schnittstelle einen speziellen Wert, z. B. 0, 1, oder – 2, statt einen Objektzeiger übergibt. Im Gegensatz zu [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], die CLR lässt keine Konstanten als Objekte umgewandelt werden. Stattdessen die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop-Assembly definiert den Parameter als ein <xref:System.IntPtr> Typ.  
  
 Verwaltete Implementierungen dieser Methoden sollten den Umstand nutzen, die die <xref:System.IntPtr> -Klasse verfügt über beide `int` und `void *` von Konstruktoren zum Erstellen einer <xref:System.IntPtr> über ein Objekt oder eine ganzzahlige Konstante, je nach Bedarf.  
  
 Verwaltete Methoden, die empfangen <xref:System.IntPtr> Parameter dieses Typs verwenden, sollten die <xref:System.IntPtr> geben Konvertierungsoperatoren, um die Ergebnisse zu verarbeiten. Konvertieren Sie zuerst die <xref:System.IntPtr> zu `int` und relevante ganzzahlige Konstanten getestet. Wenn keine Werte zusammenpassen, konvertieren Sie ihn in ein Objekt des erforderlichen Typs und fortfahren.  
  
 Beispiele hierfür finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE zurückgegeben Werte übergeben als [out]-Parameter  
 Suchen Sie nach Methoden, die eine `retval` Rückgabewert in der COM-Schnittstelle, aber das ein `int` Rückgabewert und ein zusätzliches [out] Arrayparameter in die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Methodenprototyps der interop-Assembly. Es muss klar, dass diese Methoden besondere Behandlung erfordern, da die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop-Assembly-Methodenprototypen haben einen weiteren Parameter als die COM-Schnittstellenmethoden.  
  
 Viele COM-Schnittstellen, die OLE-Aktivität behandeln senden Informationen über OLE-Status zurück an das aufrufende Programm, die in gespeicherten der `retval` Wert der Schnittstelle zurück. Anstatt einen Rückgabewert der entsprechenden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop-Assembly-Methoden senden Sie die Informationen an das aufrufende Programm in einen [Out] gespeicherten Arrayparameter.  
  
 Verwaltete Implementierungen dieser Methoden erstellen ein Array mit einzelnen Elementen des gleichen Typs als [Out]-Parameter und fügen Sie ihn in den-Parameter. Der Wert des Arrayelements muss identisch mit den entsprechenden COM `retval`.  
  
 Verwaltete Methoden, die Schnittstellen dieses Typs aufrufen sollten das erste Element aus dem [Out] Array extrahieren. Dieses Element behandelt werden kann, als wäre er ein `retval` Wert aus der entsprechenden COM-Schnittstelle zurückzugeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Interop-Marshalling](http://msdn.microsoft.com/en-us/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Interop-Marshalling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Problembehandlung bei der Interoperabilität](http://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Verwaltete VSPackages](../misc/managed-vspackages.md)