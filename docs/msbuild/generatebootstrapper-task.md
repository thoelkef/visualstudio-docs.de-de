---
title: "GenerateBootstrapper-Aufgabe | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild GenerateBootstrapper-Aufgabe"
  - "GenerateBootstrapper-Aufgabe [MSBuild]"
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateBootstrapper-Aufgabe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bietet eine automatisierte Möglichkeit zum erkennen, herunterladen und Installieren einer Anwendung und die erforderlichen Komponenten. Sie dient als einzelner Installer, der das separate Installationsprogramme für alle Komponenten einer Anwendung integriert.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `GenerateBootstrapper`-Aufgabe beschrieben.  
  
-   `ApplicationFile`  
  
     Optionaler `String` -Parameter.  
  
     Gibt die Datei, mit der Bootstrapper die Installation der Anwendung gestartet, nachdem alle erforderlichen Komponenten installiert wurden. Wenn weder ein Buildfehler führt die `BootstrapperItems` noch die `ApplicationFile` angegeben wurde.  
  
-   `ApplicationName`  
  
     Optionaler `String` -Parameter.  
  
     Gibt den Namen der Anwendung, die die vom Bootstrapper installiert wird. Dieser Name wird in der Benutzeroberfläche angezeigt, die der Bootstrapper während der Installation verwendet.  
  
-   `ApplicationRequiresElevation`  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, die Komponente mit erweiterten Berechtigungen ausgeführt wird, wenn sie auf dem Zielcomputer installiert ist.  
  
-   `ApplicationUrl`  
  
     Optionaler `String` -Parameter.  
  
     Gibt die Webadresse, die das Installationsprogramm der Anwendung gehostet wird.  
  
-   `BootstrapperComponentFiles`  
  
     Optionaler `String[]`-Ausgabeparameter.  
  
     Gibt den erstellten Speicherort der Bootstrapper-Paketdateien.  
  
-   `BootstrapperItems`  
  
     Optionale <xref:Microsoft.Build.Framework.ITaskItem>`[]` Parameter.  
  
     Gibt die Produkte in den Bootstrapper zu erstellen. Die an diesen Parameter übergebenen Elemente sollten die folgende Syntax aufweisen:  
  
    ```  
    <BootstrapperItem  
        Include="ProductCode">  
        <ProductName>  
            ProductName  
        </ProductName>  
    </BootstrapperItem>  
    ```  
  
     Die `Include` Attribut wird verwendet, um den Namen einer Vorbedingung darzustellen, die installiert werden sollte. Die `ProductName` Elementmetadaten ist optional und wird vom Buildmodul als verwendet einen benutzerfreundlichen Namen für den Fall, dass das Paket nicht gefunden werden kann. Diese Elemente sind keine erforderlichen [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Eingabeparameter, sofern keine `ApplicationFile` angegeben ist. Sie sollten ein Element für jede Vorbedingung installiert sein muss, für Ihre Anwendung einbinden.  
  
     Wenn weder ein Buildfehler führt die `BootstrapperItems` noch die `ApplicationFile` angegeben wurde.  
  
-   `BootstrapperKeyFile`  
  
     Optionaler `String`-Ausgabeparameter.  
  
     Gibt den erstellten Speicherort von setup.exe  
  
-   `ComponentsLocation`  
  
     Optionaler `String` -Parameter.  
  
     Gibt einen Speicherort für den Bootstrapper für die Installation zu installierende erforderliche Komponenten zu suchen. Dieser Parameter kann die folgenden Werte aufweisen:  
  
    -   `HomeSite`: Gibt an, dass die Vorbedingung vom Komponentenanbieter gehostet wird.  
  
    -   `Relative`: Gibt an, dass die Vorbedingung sich am gleichen Speicherort der Anwendung befindet.  
  
    -   `Absolute`: Gibt an, dass sich alle Komponenten bei einer zentralisierten URL befinden. Dieser Wert sollte verwendet werden, zusammen mit den `ComponentsUrl` Eingabeparameter.  
  
     Wenn `ComponentsLocation` nicht angegeben ist, `HomeSite` wird standardmäßig verwendet.  
  
-   `ComponentsUrl`  
  
     Optionaler `String` -Parameter.  
  
     Gibt die URL, die Voraussetzung für die Installation enthält.  
  
-   `CopyComponents`  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, kopiert der Bootstrapper alle Ausgabedateien, die im angegebenen Pfad der `OutputPath` Parameter. Die Werte der `BootstrapperComponentFiles` Parameter sollten alle werden basierend auf diesen Pfad. Wenn `false`, die Dateien werden nicht kopiert, und die `BootstrapperComponentFiles` Werte basieren auf dem Wert der `Path` Parameter.  Der Standardwert dieses Parameters ist `true`.  
  
-   `Culture`  
  
     Optionaler `String` -Parameter.  
  
     Gibt die Kultur für den Bootstrapper-Benutzeroberfläche und Installation erforderlichen Komponenten. Wenn die angegebene Kultur nicht verfügbar ist, verwendet die Aufgabe den Wert der der `FallbackCulture` Parameter.  
  
-   `FallbackCulture`  
  
     Optionaler `String` -Parameter.  
  
     Gibt die sekundäre Kultur für die Benutzeroberfläche Bootstrapper und Voraussetzung für die Installation.  
  
-   `OutputPath`  
  
     Optionaler `String` -Parameter.  
  
     Gibt den Speicherort zum Kopieren von setup.exe und alle Paketdateien.  
  
-   `Path`  
  
     Optionaler `String` -Parameter.  
  
     Gibt den Speicherort für alle verfügbaren Pakete erforderlicher Komponenten.  
  
-   `SupportUrl`  
  
     Optionaler `String` -Parameter.  
  
     Gibt die URL die Bootstrapper-Installation durchgeführt werden soll  
  
-   `Validate`  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, der Bootstrapper die XSD-Validierung der angegebenen Bootstrapper-Eingabeelemente durchführt. Der Standardwert dieses Parameters ist `false`.  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension> Klasse, die selbst erbt von der <xref:Microsoft.Build.Utilities.Task> Klasse. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `GenerateBootstrapper` Aufgabe, eine Anwendung zu installieren, müssen die [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] als erforderliche Komponente installiert.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">  
            <ProductName>Microsoft .NET Framework 2.0</ProductName>  
        </BootstrapperFile>  
    </ItemGroup>  
  
    <Target Name="BuildBootstrapper">  
        <GenerateBootstrapper  
            ApplicationFile="WindowsApplication1.application"  
            ApplicationName="WindowsApplication1"  
            ApplicationUrl="http://mycomputer"  
            BootstrapperItems="@(BootstrapperFile)"  
            OutputPath="C:\output" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgaben](../msbuild/msbuild-tasks.md)   
 [Referenz zu Aufgaben](../msbuild/msbuild-task-reference.md)