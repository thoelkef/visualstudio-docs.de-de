---
title: "Gewusst wie: Bereitstellen von benutzerdefinierten Werkzeugkastenelementen mithilfe von Interopassemblys | Microsoft Docs"
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
  - "Toolbox [Visual Studio SDK], Elemente mithilfe von Interopassemblys hinzufügen"
ms.assetid: c3e8b404-7086-4e08-9d07-ab9c509963ca
caps.latest.revision: 33
caps.handback.revision: 33
manager: "douge"
---
# Gewusst wie: Bereitstellen von benutzerdefinierten Werkzeugkastenelementen mithilfe von Interopassemblys
> [!NOTE]
>  Die empfohlene Methode zum Hinzufügen benutzerdefinierter Steuerelemente zur Toolbox ist die Verwendung der Vorlagen für Toolbox\-Steuerelemente, die im Lieferumfang des Visual Studio 10 SDK enthalten sind. Dieses Thema wird nur aus Gründen der Abwärtskompatibilität sowie des Hinzufügens von vorhandenen Steuerelementen zur Toolbox beibehalten.  
>   
>  Weitere Informationen zum Erstellen von Toolbox\-Steuerelementen mithilfe der Vorlagen finden Sie unter [Gewusst wie: Erstellen eines Toolbox\-Steuerelements, das Windows Forms verwendet](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) und [Erstellen ein WPF\-Toolbox\-Steuerelement](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Mit einem VSPackage, das auf einer Interop\-Assembly basiert, kann die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Toolbox**\-Funktionalität erweitert werden, indem ActiveX\-Steuerelemente hinzugefügt werden.  
  
 Eine Liste der standardmäßigen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Toolbox\-Zwischenablageformate finden Sie unter [Erweitern der Toolbox](../misc/extending-the-toolbox.md).  
  
 Informationen dazu, wie die **Toolbox** mit einem VSPackage über das [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] verwaltet wird, finden Sie unter [Verwalten der Toolbox](../misc/managing-the-toolbox.md).  
  
 Informationen zum Verwalten der **Toolbox** über Automatisierung finden Sie unter [Gewusst wie: Steuern der Toolbox](../Topic/How%20to:%20Control%20the%20Toolbox.md).  
  
## Verfahren  
 Elemente, die der **Toolbox** hinzugefügt werden, müssen die standardmäßigen **Toolbox**\-Zwischenablageformate implementieren, es sei denn, das VSPackage, mit dem die Elemente hinzugefügt werden, fungiert als ein **Toolbox**\-Elementanbieter – es stellt Implementierungsunterstützung für das neue Format bereit.  
  
#### So implementieren Sie ein Toolbox\-Steuerelement  
  
-   Ein **Toolbox**\-Element, das als VSPackage bereitgestellt wird, das in nicht verwaltetem Code implementiert ist, muss entweder ein `IDataObject`\-Objekt implementieren oder ein ActiveX\-Steuerelement sein, aus dem die Umgebung ein `IDataObject`\-Objekt abrufen kann.  
  
     Weitere Informationen zum Implementieren des `IDataObject` Objekts zur Unterstützung der **Toolbox** finden Sie unter <xref:System.Runtime.InteropServices.ComTypes.IDataObject>, <xref:Microsoft.VisualStudio.Shell.Interop.TBXITEMINFO> und <xref:System.Runtime.InteropServices.ComTypes.FORMATETC>.  
  
#### So fügen Sie auf Interop\-Assemblys basierende Steuerelemente zur Toolbox hinzu  
  
1.  Erstellen Sie Instanzen der:  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>\-Schnittstelle, die das Hinzufügen von Steuerelementen und Abschnitten \(Registerkarten\) zur **Toolbox** sowie das Steuern von anderen Aspekten der **Toolbox**\-Konfiguration unterstützt.  
  
    2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>\-Schnittstelle, die Unterstützung für Lokalisierung und Dauerhaftigkeit von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Einstellungen bietet.  
  
    > [!NOTE]
    >  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>\-Schnittstelle erbt von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>\-Schnittstelle.<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> wird nicht von <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> abgeleitet und implementiert nicht die zugehörigen Methoden.  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> werden zurückgegeben, indem die <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>\-Methode für den <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>\-Dienst mit Angabe der Dienst\-ID von `SID_SVsToolbox` aufgerufen wird.  
  
     Die Schnittstellen\-ID `IID_IVSToolbox2` wird verwendet, um <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> zurückzugeben, und die Schnittstellen\-ID `IID_IVSToolbox3` gibt <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> zurück.  
  
     Im folgenden Beispiel wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>Schnittstelle mit einem `QueryService` zurückgegeben, und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>\-Schnittstelle wird zurückgegeben, indem `QueryInterface` für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>\-Schnittstelle aufgerufen wird.  
  
    ```cpp  
    extern CComModule _Module;  
    CComPtr<IVsToolbox2> srpTbx2;  
    CComPtr<IVsToolbox3> srpTbx3;  
    hr = _Module.QueryService(SID_SVsToolbox, IID_IVsToolbox2, (void**) &srpTbx2));  
    hr = srpTbx2->QueryInterface( IID_IVsToolbox3, (void **)&srpTbx3)  
    ```  
  
2.  Verwenden Sie Instanzen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>\- und der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>\-Schnittstelle, um Registerkarten \(Abschnitte\) und Steuerelemente zur **Toolbox** hinzuzufügen.  
  
     Im folgenden Beispiel wird mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.AddTab%2A>\-Methode eine neue Registerkarte mit einem lokalisierten Namen hinzugefügt.  
  
     Weil dieser lokalisierte Namen nicht invariant ist, wird ein nicht lokalisierter invarianter Name \(in diesem Fall `L"HTML"`\) festgelegt, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A>\-Methode aufgerufen wird.  
  
     Ist die Toolboxregisterkarte bereits vorhanden, gibt `AddTab2` E\_FAIL zurück. In diesem Fall wird davon ausgegangen, dass die Registerkarte ordnungsgemäß hinzugefügt wurde, bevor versucht wird, den invarianten Namen abzurufen.  
  
     Wurde eine Registerkarte erfolgreich hinzugefügt, wird ein <xref:System.Runtime.InteropServices.ComTypes.IDataObject>\-basiertes Steuerelement zur **Toolbox** hinzugefügt. Andernfalls wird ein Fehler zurückgegeben.  
  
    ```cpp  
    CComBSTR sbstrID;  
    hr = srpTbx2->AddTab2((WCHAR*)szwDisplayTabName, *pclsidPackage);  
    if ( hr == S_OK) {  
        sbstrID =L"HTML";  
        hr = srpTbx3->SetIDOfTab( (WCHAR*)szwDisplayTabName, sbstrID);  
    }else{  
        hr = S_OK;  
        hr = srpTbx3->GetIDOfTab( (WCHAR*)szwDisplayTabName, &sbstrID );  
  
    }  
    if ( hr = S_OK){  
        hr=srpTbx2->AddItem(tbxItem, &tinfo, bstrLabel);  
    }  
    return hr;  
    ```  
  
 Zusätzlich dazu, dass ein VSPackage die **Toolbox** selbst erweitert, kann es als ein **Toolbox**\-Datenanbieter konfiguriert und dazu verwendet werden, die Drag & Drop\-Unterstützung auf die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE zu erweitern. Dies ermöglicht es, der **Toolbox** und Editoren beliebige Zwischenablageformate verfügbar zu machen.  
  
#### So konfigurieren Sie ein VSPackage als Toolboxelementanbieter  
  
1.  Registrieren Sie das interop\-basierte VSPackage als einen **Toolbox**\-Elementanbieter.  
  
     Weitere Informationen zum Registrieren als **Toolbox**\-Anbieter finden Sie unter [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md).  
  
2.  Registrieren Sie benutzerdefinierte **Toolbox**\-Zwischenablageformate.  
  
     Interop\-basierte VSPackages, die Steuerelemente unterstützen, für die nicht alle standardmäßigen **Toolbox**\-Zwischenablageformate implementiert sind oder für die ein benutzerdefiniertes **Toolbox**\-Zwischenablageformat implementiert ist, müssen:  
  
    1.  Die Toolbox\-Zwischenablageformate registrieren, die sie unterstützen. Weitere Informationen finden Sie unter [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md).  
  
    2.  Eine Klasse erstellen, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider>\- und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2>\-Schnittstelle implementiert.  
  
        > [!NOTE]
        >  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider>\- und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2>\-Schnittstelle sollten nicht mit der Klasse implementiert sein, in der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>\-Schnittstelle implementiert ist.  
  
    3.  Die Toolbox programmgesteuert darüber informieren, das eine bestimmte Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider>\- und der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2>\-Schnittstellen Unterstützung für benutzerdefinierte Datenformate bietet. Dazu wird eine der gleichwertigen Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry.RegisterDataProvider%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox.RegisterDataProvider%2A> verwendet.  
  
         Das Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox.RegisterDataProvider%2A>Methode erfolgt normalerweise in der Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>\-Methode oder in der <xref:Microsoft.VisualStudio.Shell.WindowPane.OnCreate%2A>\-Handlermethode, wenn das VSPackage aktiv wird.  
  
        ```cpp  
        CComPtr<IVsToolboxDataProviderRegistry> pTB;  
        if (SUCCEEDED (hr = pServiceProvider->QueryService(SID_SVsToolboxDataProviderRegistry, IID_IVsToolboxDataProviderRegistry, (PVOID*)&pTB)) && pTB != NULL)  
        {  
            CustToolboxDataProvider* pDP = new CustToolboxDataProvider;  
            if (pDP)  
            {  
                pDP->AddRef();  
                VSCOOKIE dwDPCookie; //UNDONE: pass NULL instead of ptr to the cookie when RegisterDataProvider allows it.  
                pTB->RegisterDataProvider((IVsToolboxDataProvider*)pDP, &dwDPCookie);  
                pDP->Release();  
            }  
            else  
            {  
                hr = E_OUTOFMEMORY;  
            }  
        }  
        ```  
  
 Eine Liste der standardmäßigen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-**Toolbox**\-Zwischenablageformate finden Sie unter [Erweitern der Toolbox](../misc/extending-the-toolbox.md).  
  
## Siehe auch  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)   
 [Werkzeugkasten, exemplarische Vorgehensweisen](../misc/toolbox-walkthroughs.md)   
 [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md)   
 [Erweiterte Toolbox\-Steuerelemententwicklung](../misc/advanced-toolbox-control-development.md)   
 [Verwalten der Toolbox](../misc/managing-the-toolbox.md)   
 [Gewusst wie: Steuern der Toolbox](../Topic/How%20to:%20Control%20the%20Toolbox.md)