---
title: Parametermarshalling für Visual Studio-Interop-Assemblys | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686924"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Parameter-Marshalling für Visual Studio-Interopassemblys
VSPackages, die in verwaltetem Code geschrieben werden, müssen möglicherweise aufrufen oder von nicht verwaltetem com-Code aufgerufen werden. Normalerweise werden Methodenargumente vom Interop-Mars Haller automatisch transformiert oder gemarshallt. Manchmal können Argumente jedoch nicht auf einfache Weise transformiert werden. In diesen Fällen werden die Parameter der Interop-Assemblymethode Prototype verwendet, um die com-Funktionsparameter so genau wie möglich abzugleichen. Weitere Informationen finden Sie unter [Interop](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)-Marshalling.  
  
## <a name="general-suggestions"></a>Allgemeine Vorschläge  
  
##### <a name="read-the-reference-documentation"></a>Referenz Dokumentation lesen  
 Eine effektive Möglichkeit zur Erkennung von Interoperabilitätsproblemen ist das Lesen der Referenz Dokumentation für jede Methode.  
  
 Die Referenz Dokumentation für jede Methode enthält drei relevante Abschnitte:  
  
- Der [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Prototyp der com-Funktion.  
  
- Der Interop-AssemblyMethoden Prototyp.  
  
- Eine Liste der com-Parameter und eine kurze Beschreibung der einzelnen Parameter.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Suchen nach Unterschieden zwischen den beiden Prototypen  
 Die meisten Interoperabilitätsprobleme werden von Konflikten zwischen der Definition eines bestimmten Typs in einer COM-Schnittstelle und der Definition desselben Typs in den Interop-Assemblys abgeleitet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Beachten Sie z. b. den Unterschied in der Möglichkeit, einen `null` Wert in einen [out]-Parameter zu übergeben. Sie müssen nach Unterschieden zwischen den beiden Prototypen suchen und deren Auswirkungen für die übergebenen Daten abwägen.  
  
##### <a name="read-the-parameter-definitions"></a>Lesen der Parameter Definitionen  
 Lesen Sie die Parameter Definitionen. COM ist weniger streng als die Common Language Runtime (CLR) zum Mischen verschiedener Datentypen in einem einzelnen Parameter. Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] com-Schnittstellen nutzen diese Flexibilität in vollem Umfang. Jeder Parameter, der einen nicht standardmäßigen Wert oder Datentyp, z. b. ein konstanter Wert in einem Zeiger Parameter, übergeben oder erfordern kann, sollte in der-Dokumentation als solches beschrieben werden.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>IUnknown-Objekte, die als Typ void * * übertragen wurden  
 Suchen Sie nach [out]-Parametern, die `void **` in der COM-Schnittstelle als Typ definiert sind, aber `[``iid_is``]` im-Prototyp der Interop-Assemblymethode als definiert sind [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Manchmal generiert eine COM-Schnittstelle ein `IUnknown` Objekt, und die COM-Schnittstelle übergibt sie als Typ `void **` . Diese Schnittstellen sind besonders wichtig, denn wenn die Variable als [out] in der IDL definiert ist, `IUnknown` wird das Objekt mit der-Methode auf Verweis gezählt `AddRef` . Ein Speicherfehler tritt auf, wenn das Objekt nicht ordnungsgemäß behandelt wird.  
  
> [!NOTE]
> Ein `IUnknown` Objekt, das von der COM-Schnittstelle erstellt und in einer [out]-Variablen zurückgegeben wird, verursacht einen Speicherlecks, wenn es nicht explizit freigegeben wird  
  
 Verwaltete Methoden, die solche Objekte verarbeiten <xref:System.IntPtr> , sollten als Zeiger auf ein `IUnknown` -Objekt behandeln und die- <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Methode zum Abrufen des-Objekts aufzurufen. Der Aufrufer sollte dann den Rückgabewert in den entsprechenden Typ umwandeln. Wenn das Objekt nicht mehr benötigt wird, wird aufgerufen, <xref:System.Runtime.InteropServices.Marshal.Release%2A> um es freizugeben.  
  
 Im folgenden finden Sie ein Beispiel für das Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> -Methode und das korrekte behandeln des- `IUnknown` Objekts:  
  
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
> Die folgenden Methoden sind bekannt, dass `IUnknown` Objekt Zeiger als Typ übergeben werden <xref:System.IntPtr> . Behandeln Sie Sie wie in diesem Abschnitt beschrieben.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>Optionale [out]-Parameter  
 Suchen Sie nach Parametern, die als [out]-Datentyp ( `int` , `object` usw.) in der COM-Schnittstelle definiert sind, jedoch als Arrays desselben Datentyps im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interopassemblymethode-Prototyp definiert sind.  
  
 Einige COM-Schnittstellen, wie z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> . b., behandeln [out]-Parameter als optional. Wenn ein Objekt nicht erforderlich ist, geben diese COM-Schnittstellen einen `null` Zeiger als Wert dieses Parameters zurück, anstatt das [out]-Objekt zu erstellen. Dies ist beabsichtigt. Für diese Schnittstellen `null` werden Zeiger als Teil des korrekten Verhaltens des VSPackages angenommen, und es wird kein Fehler zurückgegeben.  
  
 Da die CLR den Wert eines [out]-Parameters nicht zulässt `null` , ist ein Teil des entworfenen Verhaltens dieser Schnittstellen nicht direkt in verwaltetem Code verfügbar. Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Interop-AssemblyMethoden für betroffene Schnittstellen umgehen das Problem, indem die relevanten Parameter als Arrays definiert werden, da die CLR das Übergeben von `null` Arrays zulässt.  
  
 Verwaltete Implementierungen dieser Methoden sollten ein- `null` Array in den-Parameter einfügen, wenn nichts zurückgegeben werden muss. Andernfalls erstellen Sie ein Array mit einem Element des richtigen Typs und fügen den Rückgabewert in das Array ein.  
  
 Verwaltete Methoden, die Informationen von Schnittstellen mit optionalen [out]-Parametern empfangen, empfangen den Parameter als Array. Überprüfen Sie einfach den Wert des ersten Elements des Arrays. Wenn dies nicht der Fall ist `null` , behandeln Sie das erste Element, als wäre es der ursprüngliche Parameter.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Übergeben von Konstanten in Zeiger Parametern  
 Suchen Sie nach Parametern, die in der COM-Schnittstelle als [in]-Zeiger definiert sind, die <xref:System.IntPtr> im-Prototyp der interopassemblymethode als Typ definiert sind [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Ein ähnliches Problem tritt auf, wenn eine COM-Schnittstelle einen speziellen Wert, z. b. 0,-1 oder – 2, anstelle eines Objekt Zeigers übergibt. Im Gegensatz [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] zu lässt die CLR nicht zu, dass Konstanten als-Objekte umgewandelt werden. Stattdessen definiert die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Interop-Assembly den Parameter als <xref:System.IntPtr> Typ.  
  
 Verwaltete Implementierungen dieser Methoden sollten die Tatsache nutzen, dass die <xref:System.IntPtr> -Klasse sowohl `int` -als auch- `void *` Konstruktoren besitzt <xref:System.IntPtr> , um entweder aus einem Objekt oder einer ganzzahligen Konstante zu erstellen.  
  
 Verwaltete Methoden, die <xref:System.IntPtr> Parameter dieses Typs empfangen, sollten die <xref:System.IntPtr> Typkonvertierungs Operatoren verwenden, um die Ergebnisse zu verarbeiten. Konvertieren Sie zuerst den <xref:System.IntPtr> in, `int` und testen Sie ihn anhand relevanter ganzzahliger Konstanten. Wenn keine Werte gefunden werden, konvertieren Sie Sie in ein Objekt des erforderlichen Typs, und fahren Sie fort.  
  
 Beispiele hierfür finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>Als [out] Parameter über gegebene OLE-Rückgabewerte  
 Suchen Sie nach Methoden, die über einen `retval` Rückgabewert in der COM-Schnittstelle verfügen, aber einen `int` Rückgabewert und einen zusätzlichen [out]-Array Parameter im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interopassemblymethode-Prototyp aufweisen. Es sollte klar sein, dass diese Methoden eine besondere Behandlung erfordern, da die Methoden der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interopassemblymethode einen größeren Parameter aufweisen als die COM-Schnittstellen Methoden.  
  
 Viele COM-Schnittstellen, die die OLE-Aktivität behandeln, senden Informationen zum OLE-Status zurück an das aufrufende Programm, das im `retval` Rückgabewert der Schnittstelle gespeichert ist. Anstatt einen Rückgabewert zu verwenden, senden die entsprechenden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Interop-AssemblyMethoden die Informationen an das aufrufende Programm zurück, das in einem [out]-Array Parameter gespeichert ist.  
  
 Verwaltete Implementierungen dieser Methoden sollten ein Array mit einem einzelnen Element desselben Typs wie der [out]-Parameter erstellen und im-Parameter ablegen. Der Wert des Array Elements muss mit dem entsprechenden com identisch sein `retval` .  
  
 Verwaltete Methoden, die Schnittstellen dieses Typs aufzurufen, sollten das erste Element aus dem [out]-Array abrufen. Dieses Element kann so behandelt werden, als ob es ein `retval` Rückgabewert von der entsprechenden COM-Schnittstelle wäre.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Interop-Marshalling](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Interop-Marshalling](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Problembehandlung bei Interoperabilität](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Verwaltete VSPackages](../misc/managed-vspackages.md)