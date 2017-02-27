---
title: "Registrieren von Einzeldatei-Generatoren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Benutzerdefinierte Tools-Registrierung"
  - "Benutzerdefinierte Tools, definieren Einstellungen in der Registrierung"
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Registrieren von Einzeldatei-Generatoren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein benutzerdefiniertes Tool in zur Verfügung gestellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], Sie müssen ihn also registrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können instanziieren und einen bestimmten Projekttyp zugeordnet.  
  
### Registrieren Sie ein benutzerdefiniertes tool  
  
1.  Registrieren Sie das benutzerdefinierte Tool DLL entweder in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokale Registrierung oder in der Registrierung, unter HKEY\_CLASSES\_ROOT.  
  
     Hier ist z. B. die Registrierungsinformationen für das verwaltete MSDataSetGenerator benutzerdefinierte Tool, das im Lieferumfang [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Erstellen Sie einen Registrierungsschlüssel in der gewünschten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hive unter Generators\\*GUID* *GUID* ist die GUID vom Projektsystem der jeweilige Sprache oder vom Dienst definiert. Der Name des Schlüssels wird der programmgesteuerte Name des benutzerdefinierten Tools. Der benutzerdefinierte Tool Schlüssel hat die folgenden Werte:  
  
    -   \(Standard\)  
  
         Optional. Bietet eine benutzerfreundliche Beschreibung des benutzerdefinierten Tools. Dieser Parameter ist optional, jedoch empfohlen.  
  
    -   CLSID  
  
         Erforderlich. Gibt den Bezeichner der COM\-Komponente, implementiert der Klassenbibliothek <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    -   GeneratesDesignTimeSource  
  
         Erforderlich. Gibt an, ob Typen von Dateien, die von diesem benutzerdefinierten Tool visuellen Designern zur Verfügung gestellt werden. Der Wert dieses Parameters muss \(null\) 0 für Typen, die für visuelle Designer nicht verfügbar sind oder für Typen, die visuellen Designern zur Verfügung \(1\) 1 sein.  
  
    > [!NOTE]
    >  Sie müssen das benutzerdefinierte Tool für jede Sprache einzeln registrieren, für die das benutzerdefinierte Tool verfügbar sein soll.  
  
     Zum Beispiel registriert die MSDataSetGenerator selbst einmal für jede Sprache:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementieren von Einzeldatei\-Generatoren](../../extensibility/internals/implementing-single-file-generators.md)   
 [Ermitteln des Standardnamespaces eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)   
 [\-Typen für visuelle Designer verfügbar gemacht](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Einführung in das BuildManager\-Objekt](http://msdn.microsoft.com/de-de/50080ec2-c1c9-412c-98ef-18d7f895e7fa)