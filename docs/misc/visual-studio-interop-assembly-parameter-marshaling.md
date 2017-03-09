---
title: "Parameter-Marshalling f&#252;r Visual Studio-Interopassemblys | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Problembehandlung bei Visual Studio SDK-Interopassemblys"
  - "Interopassemblys, Parameter-Marshalling"
  - "Interopassemblys, Problembehandlung"
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Parameter-Marshalling f&#252;r Visual Studio-Interopassemblys
VSPackages, die in verwaltetem Code geschrieben wurden oder aufrufen müssen, kann durch nicht verwalteten COM\-Code aufgerufen werden.  In der Regel werden Methodenargumente Transformationen oder gemarshallt, automatisch durch den Interop\-Marshaller.  Manchmal können Argumente nicht in einer einfachen Typ umgewandelt werden.  In diesen Fällen werden die Interop\-Assembly methoden\-Prototyp Zeichenfolgenparameter verwendet, um die COM\-Funktionsparameter so genau wie möglich zu entsprechen.  Weitere Informationen finden Sie unter [Interop Marshaling](../Topic/Interop%20Marshaling.md).  
  
## Allgemeine Empfehlungen  
  
##### Lesen Sie in der Referenzdokumentation  
 Eine effektive Möglichkeit, Interoperabilitätsprobleme zu erkennen ist, die Referenzdokumentation für jede Methode zu lesen.  
  
 Die Referenzdokumentation für jede Methode enthält drei relevante Abschnitte:  
  
-   Der Funktionsprototyp [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] COM.  
  
-   Der Interop\-Assembly Methode prototyp.  
  
-   Eine Liste der COM\-Parameter und der Kurzbeschreibung jeder.  
  
##### Suchen Sie nach Unterschieden zwischen den zwei Prototypen  
 Die meisten Interoperabilitätsprobleme leiten sich von den Konflikten zwischen der Definition eines bestimmten Typs in einer COM\-Schnittstelle und die Definition von demselben Typ in die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assemblys ein.  Betrachten Sie beispielsweise den Unterschied in der Möglichkeit, einen `null`\-Wert in einem \[out\] Parameter zu übergeben.  Sie müssen nach Unterschieden zwischen den zwei Prototypen suchen und ihre Verzweigungen für die Daten, die übergeben werden.  
  
##### Lesen Sie die Parameterdefinitionen  
 Lesen Sie die Parameterdefinitionen.  COM ist weniger strikt als die Common Language Runtime \(CLR\) zum Kombinieren unterschiedlicher Typen von Daten in einem einzelnen Parameter.  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] COM\-Schnittstellen ziehen die Vorteile dieser Flexibilität.  Jeder Parameter, der übergeben kann, oder einen nicht standardmäßigen Wert benötigt oder Typ der Daten, z. B. einen konstanten Wert in einen Zeigerparameter, sollte als solche in der Dokumentation beschrieben werden.  
  
### Übergabe als Typ void \*\* IUnknown\-Objekte  
 Suchen Sie \[out\] nach Parametern, die als Typ `void **` in der COM\-Schnittstelle definiert werden, aber die als `[``iid_is``]` im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assembly Methode prototyp definiert sind.  
  
 In manchen Fällen generiert eine COM\-Schnittstelle ein `IUnknown`\-Objekt, und die COM\-Schnittstelle wird es als Typ `void **`.  Diese Schnittstellen sind, da besonders wichtig, wenn die Variable wie \[out\] in der IDL\-Datei definiert ist, das `IUnknown`\-Objekt mit der `AddRef`\-Methode REFERENCE\-gezählt wird.  Ein Speicherverlust tritt auf, wenn das Objekt nicht ordnungsgemäß behandelt wird.  
  
> [!NOTE]
>  Ein `IUnknown`\-Objekt, das von der COM\-Schnittstelle erstellt und in einer \[out\] Variablen zurückgegeben wurde, führt zu einem Speicherverlust, wenn es nicht explizit freigegeben wird.  
  
 Verwaltete Methoden, die diese Objekte verarbeiten, sollten <xref:System.IntPtr> z. B. ein Zeiger auf ein `IUnknown`\-Objekts behandeln und rufen die <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>\-Methode aufgerufen, um das Objekt abzurufen.  Der Aufrufer sollte den Rückgabewert Typ umwandeln, dann angemessen ist.  Wenn das Objekt nicht mehr benötigt wird, rufen Sie <xref:System.Runtime.InteropServices.Marshal.Release%2A> an, um es freizugeben.  
  
 Das folgende Beispiel veranschaulicht die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>\-Methode ordnungsgemäß aus aufrufen und das `IUnknown`\-Objekt behandeln:  
  
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
>  Die folgenden Methoden sind als `IUnknown`\-Objektzeiger als Typ <xref:System.IntPtr>zu übergeben.  Behandeln Sie sie, wie in diesem Abschnitt beschrieben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### Optionale \[out\] Parameter  
 Suchen Sie nach Parametern, die als Datentyp \( \[out\]`int`, `object`usw.\) in der COM\-Schnittstelle definiert werden, aber die als Arrays desselben Datentyps in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assembly Methode prototyp definiert sind.  
  
 Einige COM\-Schnittstellen, wie <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>Parameter behandeln \[out\] , als optional.  Wenn ein Objekt nicht erforderlich ist, geben diese COM\-Schnittstellen einen `null` Zeiger als Wert dieses Parameters zurück, statt das \[out\] Objekt zu erstellen.  Dieser Fehler ist entwurfsbedingt.  Für diese Schnittstellen werden `null` Zeiger als Teil des ordnungsgemäßen Verhaltens angenommen, VSPackages und kein Fehler zurückgegeben.  
  
 Da die CLR nicht dem Wert eines \[out\] Parameters ermöglicht, `null`ist, ist der Teil des entworfenen Verhaltens dieser Schnittstellen nicht direkt innerhalb des verwalteten Code verfügbar.  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assembly Methoden für betroffene Schnittstellen arbeiten um das Problem, indem sie die relevanten Parameter als Arrays definieren, da die CLR die Übergabe von Arrays `null` zulässig.  
  
 Verwaltete Implementierungen dieser Methoden sollten im Array `null`\-Parameter stellen, wenn es gibt keine zurückgegeben werden soll.  Andernfalls erstellen Sie ein Einelementarray des richtigen Typs und setzen Sie den Rückgabewert in das Array ein.  
  
 Verwaltete Methoden, die Informationen aus den Schnittstellen mit optionalen \[out\] Parametern erhalten, erhalten den Parameter als Array.  Überprüfen Sie einfach den Wert des ersten Elements im Array.  Wenn dies nicht `null`ist, behandeln Sie das erste Element, als wäre es der erste Parameter war.  
  
### Übergeben von Konstanten in Zeiger\-Parametern  
 Suchen Sie nach Parametern, die als \[in\] Zeiger in der COM\-Schnittstelle definiert werden, die als <xref:System.IntPtr> definierten Methoden in den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assembly prototyp.  
  
 Ein Ähnliches Problem tritt auf, wenn eine COM\-Schnittstelle ein spezieller Wert, z. B. 0, \-1 oder 2 übergibt, anstelle eines Objektzeigers auf.  Im Gegensatz zu [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]kann die CLR nicht die Konstanten als Objekte umgewandelt werden können.  Stattdessen wird die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assembly den Parameter als <xref:System.IntPtr>\-Typ.  
  
 Verwaltete Implementierungen dieser Methoden sollten entsprechend der Tatsache genutzt, dass die <xref:System.IntPtr>\-Klasse `int` und `void *`\-Konstruktoren, um <xref:System.IntPtr> entweder von einem Objekt oder einer ganzzahligen Konstanten erstellt hat.  
  
 Verwaltete Methoden, die <xref:System.IntPtr>\-Parameter dieses Typs empfangen, sollten die <xref:System.IntPtr>\-Typkonvertierungs Operatoren verwenden, um die Ergebnisse zu behandeln.  <xref:System.IntPtr> konvertieren Sie zuerst in `int` und testen Sie es mit relevanten ganzzahlige Konstanten.  Wenn keine Werte übereinstimmen, konvertieren Sie es in ein Objekt des erforderlichen Typs und Fortfahren.  
  
 Beispiele finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> und dieses <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### OLE\-Rückgabewerte als \[out\] Parameter übergeben.  
 Suchen Sie nach Methoden, die einen `retval` Rückgabewert in der COM\-Schnittstelle verfügen, aber die einen `int` Rückgabewert und einen zusätzlichen \[out\] Arrayparameter im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assembly Methode prototyp verfügen.  Es sollte eindeutig sein, dass diese Methoden besondere Behandlung erfordern, da die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assembly Methode prototypen einen anderen Parameter als die COM\-Schnittstellen\-Methoden haben.  
  
 Viele COM\-Schnittstellen, die OLE\-Aktivität arbeiten, senden Informationen zu OLE\-Status wieder an das aufrufende Programm, das im `retval` Rückgabewert der Schnittstelle gespeichert wird.  Statt einen Rückgabewert zu verwenden, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assembly Methoden senden die entsprechenden Informationen an den aufrufenden Programm, das in einem \[out\] Arrayparameter gespeichert wird.  
  
 Verwaltete Implementierungen dieser Methoden sollten ein Array mit einem Element des gleichen Typs wie der \[out\] Parameter erstellen und es in den Parametern versehen.  Der Wert des Arrayelements sollte der gleiche wie der entsprechende COM `retval`sein.  
  
 Verwaltete Methoden, die Schnittstellen dieses Typs aufrufen, müssen das erste Element des \[out\] Arrays herausziehen.  Dieses Element kann behandelt werden, als ob es ein `retval` Rückgabewert der entsprechenden COM\-Schnittstelle war.  
  
## Siehe auch  
 [Interop Marshaling](http://msdn.microsoft.com/de-de/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Interop Marshaling](../Topic/Interop%20Marshaling.md)   
 [Troubleshooting Interoperability](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)   
 [Verwaltete VSPackages](../misc/managed-vspackages.md)