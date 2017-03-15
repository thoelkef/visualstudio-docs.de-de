---
title: "Gewusst wie: Bearbeiten von Web.Config-Dateien zur Instrumentierung und Profilerstellung f&#252;r dynamisch kompilierte ASP.NET-Webanwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Bearbeiten von Web.Config-Dateien zur Instrumentierung und Profilerstellung f&#252;r dynamisch kompilierte ASP.NET-Webanwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Instrumentationsmethode der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools zum Sammeln ausführlicher Zeitsteuerungsdaten, .NET\-Speicherbelegungsdaten und .NET\-Objektlebensdauerdaten aus dynamisch kompilierten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen verwenden.  
  
 In diesem Thema wird beschrieben, wie die Konfigurationsdatei "web.config" geändert wird, um die Instrumentation und die Profilerstellung von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen zu aktivieren.  
  
> [!NOTE]
>  Es ist nicht erforderlich, die Datei "web.config" zu ändern, wenn Sie die Samplingprofilerstellungsmethode verwenden oder wenn Sie ein vorkompiliertes [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Modul instrumentieren möchten.  
  
 Das Stammelement einer web.config\-Datei ist das **configuration**\-Element.  Zum Instrumentieren und Profilieren einer dynamisch kompilierten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung, müssen Sie die folgenden Elemente hinzufügen oder ändern:  
  
-   Ein **configuration\/runtime\/assemblyBinding\/dependentAssembly**\-Element, das die Microsoft.VisualStudio.Enterprise.ASPNetHelper\-Assembly identifiziert, die die Profilerstellung steuert.  Das **dependentAssembly**\-Element enthält zwei untergeordnete Elemente: **assemblyIdentity** und **codeBase**.  
  
-   Ein **configuration\/system.web\/compilation**\-Element, das den Nachbearbeitungskompilierungsschritt des Profilers für die Zielassembly identifiziert.  
  
-   Dem Abschnitt **configuration\/appSettings** werden zwei **add**\-Elemente hinzugefügt, die den Speicherort der Profilerstellungstools identifizieren.  
  
 Es empfiehlt sich, eine Kopie der ursprünglichen web.config\-Datei zu erstellen, mit der Sie die Konfiguration der Anwendung wiederherstellen können.  
  
### So fügen Sie die ASPNetHelper\-Assembly als configuration\/runtime\/assemblyBinding\/dependentAssembly\-Element hinzu  
  
1.  Fügen Sie das **runtime**\-Element als untergeordnetes Element des **configuration**\-Elements hinzu, falls notwendig; wechseln Sie andernfalls zum nächsten Schritt.  
  
     Das **runtime**\-Element weist keine Attribute auf.  Das **configuration**\-Element darf nur ein untergeordnetes **runtime**\-Element enthalten.  
  
2.  Fügen Sie ggf. das **assemblyBinding**\-Element als untergeordnetes Element des **runtime**\-Elements hinzu; fahren Sie andernfalls mit dem nächsten Schritt fort.  
  
     Das **runtime**\-Element darf nur ein **assemblyBinding**\-Element enthalten.  
  
3.  Fügen Sie dem **assemblyBinding**\-Element den folgenden Attributnamen und \-wert hinzu:  
  
    |Attributname|Attributwert|  
    |------------------|------------------|  
    |**Xmlns**|**urn:schemas\-microsoft\-com:asm.v1**|  
  
4.  Fügen Sie ein **dependentAssembly**\-Element als untergeordnetes Element des **assemblyBinding**\-Elements hinzu.  
  
     Das **dependentAssembly**\-Element weist keine Attribute auf.  
  
5.  Fügen Sie ein **assemblyIdentity**\-Element als untergeordnetes Element des **dependentAssembly**\-Elements hinzu.  
  
6.  Fügen Sie dem **assemblyIdentity**\-Element die folgenden Attributnamen und \-werte hinzu:  
  
    |Attributname|Attributwert|  
    |------------------|------------------|  
    |**name**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**culture**|**Neutral**|  
  
7.  Fügen Sie ein **codeBase**\-Element als untergeordnetes Element des **dependentAssembly**\-Elements hinzu.  
  
8.  Fügen Sie dem **codeBase**\-Element die folgenden Attributnamen und \-werte hinzu:  
  
    |Attributname|Attributwert|  
    |------------------|------------------|  
    |**version**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` ist die Datei\-URL von Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll.  Wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] am Standardspeicherort installiert ist, sollte der **href**\-Wert `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL` lauten.  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### So fügen Sie dem configuration\/system.web\/compilation\-Element den Nachbearbeitungsschritt des Profilers hinzu  
  
1.  Fügen Sie das **system.web**\-Element als untergeordnetes Element des **configuration**\-Elements hinzu, falls notwendig; wechseln Sie andernfalls zum nächsten Schritt.  
  
     Das **system.web**\-Element weist keine Attribute auf.  Das **configuration**\-Element darf nur ein untergeordnetes **system.web**\-Element enthalten.  
  
2.  Fügen Sie ggf. das **compilation**\-Element als untergeordnetes Element des **system.web**\-Elements hinzu; fahren Sie andernfalls mit dem nächsten Schritt fort.  
  
     Das **system.web**\-Element darf nur ein untergeordnetes **compilation**\-Element enthalten.  
  
3.  Entfernen Sie alle vorhandenen Attribute aus dem **compilation**\-Element, und fügen Sie den folgenden Attributnamen und \-wert hinzu:  
  
    |Attributname|Attributwert|  
    |------------------|------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version\=10.0.0.0, Culture\=neutral, PublicKeyToken\=b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### So fügen Sie dem configuration\/appSettings\-Element Profilerspeicherorteinstellungen hinzu  
  
1.  Fügen Sie ggf. das **appSettings**\-Element als untergeordnetes Element des **configuration**\-Elements hinzu; fahren Sie andernfalls mit dem nächsten Schritt fort.  
  
     Das **appSettings**\-Element weist keine Attribute auf.  Das **configuration**\-Element darf nur ein untergeordnetes **appSettings**\-Element enthalten.  
  
2.  Fügen Sie ein **add**\-Element als untergeordnetes Element des **appSettings**\-Elements hinzu.  
  
3.  Fügen Sie dem **add**\-Element die folgenden Attributnamen und \-werte hinzu:  
  
    |Attributname|Attributwert|  
    |------------------|------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**value**|`PerformanceToolsFolder` **\\VSInstr.Exe**|  
  
4.  Fügen Sie ein anderes **add**\-Element als untergeordnetes Element des **appSettings**\-Elements hinzu.  
  
5.  Fügen Sie diesem **add**\-Element die folgenden Attributnamen und \-werte hinzu:  
  
    |Attributname|Attributwert|  
    |------------------|------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**value**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` ist der Pfad der ausführbaren Profilerdateien.  Wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] am Standardspeicherort installiert ist, lautet der Wert **C:\\Program Files\\Microsoft Visual Studio 10.0\\Team Tools\\Performance Tools**  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## Beispiel  
 Im Folgenden ist eine vollständige web.config\-Datei dargestellt, die die Instrumentation und Profilerstellung dynamisch kompilierter [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen ermöglicht.  In diesem Beispiel wird davon ausgegangen, dass keine anderen Einstellungen in der Datei vor der Änderung vorhanden waren.  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## Siehe auch  
 [Gewusst wie: Instrumentieren einer dynamisch kompilierten ASP.NET\-Anwendung und Sammeln von ausführlichen Zeitsteuerungsdaten](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)   
 [Gewusst wie: Instrumentieren einer dynamisch kompilierten ASP.NET\-Anwendung und Sammeln von Speicherdaten](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)