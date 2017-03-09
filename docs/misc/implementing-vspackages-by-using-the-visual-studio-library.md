---
title: "Implementieren von VSPackages mithilfe der Visual Studio-Bibliothek | Microsoft Docs"
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
  - "Visual Studio-Bibliothek, Implementieren von VSPackages"
ms.assetid: 4cbac13f-2a9d-4955-b411-dad79081fdeb
caps.latest.revision: 7
caps.handback.revision: 7
manager: "douge"
---
# Implementieren von VSPackages mithilfe der Visual Studio-Bibliothek
Die `IVsPackageImpl`\-Klasse in der Visual Studio\-Bibliothek stellt eine minimale Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>\-Schnittstelle.  `IVsPackageImpl` selbst werden die meisten Methoden zum Verwalten von <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  Andere Möglichkeiten, die Sie benötigen, um zu überschreiben, um ein sinnvolles folgende Implementierung bereitzustellen:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.CreateTool%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
    > [!NOTE]
    >  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] den gesamten Code generiert Paket\-Vorlage hier erläutert wird.  Sie können auch Zeit sparen, indem Sie die Vorlage verwenden, um ein VSPackage für Sie generiert.  
  
 Pakete, die implementiert werden, indem Sie in der Regel die Visual Studio\-Bibliothek verwendet, erben eine VSPackage\-Klasse von [CComObjectRootEx Class](/visual-cpp/atl/reference/ccomobjectrootex-class) ATL und [CComCoClass Class](/visual-cpp/atl/reference/ccomcoclass-class) IVsPackageImpl und der Visual Studio\-Bibliothek.  Beispielsweise ist das Reference.Package\-Beispiel vom VSPackage\-Klassendeklaration die Folgenden:  
  
```  
class ATL_NO_VTABLE BasicPackage :   
    public CComObjectRootEx<CComSingleThreadModel>,  
    public CComCoClass<BasicPackage, &CLSID_BasicPackage>,  
    public IVsPackageImpl<BasicPackage, &CLSID_BasicPackage>,  
    ...  
```  
  
 Die `IVsPackageImpl` Vorlagenparameter, die angezeigt werden, sind die VSPackage\-Klasse selbst und ein Zeiger auf eine GUID, die ein VSPackage identifiziert.  
  
## Unterstützung COM\-Zuordnungen mit QueryInterface  
 Um Unterstützung für ATL `QueryInterface`abzurufen, muss die COM\-Zuordnung die Schnittstellen auf die von der Klasse implementiert wird.  Beispielsweise ist das Folgen die COM\-Zuordnung für die VSPackage\-Klasse im Reference.Package\-Beispiel:  
  
```  
BEGIN_COM_MAP(BasicPackage)  
    COM_INTERFACE_ENTRY(IVsPackage)  
    ...  
END_COM_MAP()  
```  
  
 Weitere Informationen über COM\-Zuordnungen, finden Sie unter [Implementing CComObjectRootEx](/visual-cpp/atl/implementing-ccomobjectrootex) und [COM\_INTERFACE\_ENTRY Macros](../Topic/COM_INTERFACE_ENTRY%20Macros.md).  
  
## Registrierung mit Registrierungs\-Karten unterstützen  
 Visual Studio\-Bibliothek ATL\-Format verwendet, um Dateien .RGS Registrierung von COM\-Objekten zu unterstützen.  Um die Token in der .RGS\-Datei zu unterstützen, verwendet Visual Studio\-Bibliothek Registrierungsdaten ist.  Registrierung ist führen die zu ersetzende auf Symbole, und unterstützen die Verwendung von IDs für Zeichenfolgentabellen Ressourcen frei.  
  
 Beispielsweise ist das Folgen die Registrierung für die VSPackage\-Klasse im Reference.Package\-Beispiel zugeordnet:  
  
```  
VSL_BEGIN_REGISTRY_MAP(IDR_BASICPACKAGE_RGS)  
    VSL_REGISTRY_MAP_GUID_ENTRY(CLSID_BasicPackage)  
    VSL_REGISTRY_RESOURCE_STRING_ENTRY(IDS_BASICPACKAGE_REGISTRY_NAME)  
    ...  
VSL_END_REGISTRY_MAP()  
```  
  
## Siehe auch  
 [VSSDK\-Beispiele](../misc/vssdk-samples.md)