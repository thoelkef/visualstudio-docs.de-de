---
title: Migrieren von apps zum universelle Windows-Plattform (UWP) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60951091914474f07f19672799fb59c8b2d0aa56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919141"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migrieren von Apps in die universelle Windows-Plattform (UWP)
Nehmen Sie die erforderlichen manuellen Änderungen an Ihren vorhandenen Projektdateien für Windows Store 8.1-Apps, Windows Phone 8.1-Apps oder mit Visual Studio 2015 RC erstellte universelle Windows-Apps vor, damit sie mit Visual Studio 2015 RTM verwendet werden können. (Wenn Sie über eine universelle Windows 8.1-App mit einem Windows-Anwendungsprojekt und einem Windows Phone-Projekt verfügen, müssen Sie die Schritte befolgen, um jedes Projekt zu migrieren).

 Mit der universellen Windows-Plattform können Sie Ihre App auf mindestens eine Gerätefamilie abzielen. Weitere Informationen zu universellen Windows-Apps finden Sie in diesem [Plattform-Handbuch](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

- [Migrieren Sie Ihre vorhandenen C#/VB-Windows Store 8.1- oder -Windows Phone 8.1-Apps](#MigrateCSharp) , um die universelle Windows-Plattform zu verwenden.

- [Migrieren Sie Ihre vorhandenen C++-Windows Store 8.1- oder -Windows Phone 8.1-Apps](#MigrateCPlusPlus) , um die universelle Windows-Plattform zu verwenden.

- [Erforderliche Änderungen für vorhandene universelle Windows-apps, die mit Visual Studio 2015 RC erstellt wurden](#PreviousVersions).

- [Erforderliche Änderungen für vorhandene Komponententestprojekte für mit Visual Studio 2015 RC erstellte universelle Windows-Apps](#MigrateUnitTest).

  Wenn Sie diese Änderungen nicht alle vornehmen möchten, erfahren Sie hier mehr über das [Portieren Ihrer vorhandenen Apps](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) in ein neues universelles Windows-Projekt.

## <a name="migrate-your-cvb-windows-store-81-or-windows-phone-81-apps-to-use-the-universal-windows-platform"></a><a name="MigrateCSharp"></a> Migrieren Ihrer c#-/VB Windows Store 8,1-oder Windows Phone 8,1-Apps zur Verwendung der universelle Windows-Plattform

#### <a name="migrate-your-cvb-project-files"></a>Migrieren Ihrer C#/VB-Projektdateien

1. Um zu erfahren, welche universelle Windows-Plattform installiert ist, öffnen Sie diesen Ordner: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Er enthält eine Liste der Ordner für jede universelle Windows-Plattform, die installiert ist. Der Ordnername ist die Version der universellen Windows-Plattform, die installiert ist. Auf diesem Windows 10-Gerät beispielsweise ist die Version 10.0.10240.0 der universellen Windows-Plattform installiert.

     ![Den Ordner öffnen, um die installierten Versionen anzuzeigen](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Es kann mehr als eine Version der universellen Windows-Plattform installiert sein. Es wird empfohlen, dass Sie die neueste Version für Ihre App verwenden.

2. Wechseln Sie mithilfe des Datei-Explorers zum Ordner, in dem Ihr UWP-Projekt gespeichert ist. Erstellen Sie eine JSON-Datei in diesem Ordner. Benennen Sie die Datei „project.json“, und fügen Sie der Datei anschließend den folgenden Inhalt hinzu:

    ```json
    {
      "dependencies": {
        "Microsoft.ApplicationInsights": "1.0.0",
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
      },
      "frameworks": {
        "uap10.0": {}
      },
      "runtimes": {
        "win10-arm": {},
        "win10-arm-aot": {},
        "win10-x86": {},
        "win10-x86-aot": {},
        "win10-x64": {},
        "win10-x64-aot": {}
      }
    }

    ```

3. Erstellen Sie eine Datei namens „default.rd.xml“ mit dem folgenden Inhalt. Wenn Sie über ein VB-Projekt verfügen, fügen Sie diese Datei in das Verzeichnis „Mein Projekt“ für das Projekt hinzu. Wenn Sie über ein C#-Projekt verfügen, fügen Sie diese Datei in das Verzeichnis „Eigenschaften“ für das Projekt hinzu.

    ```xml
    <?xml version="1.0"?>
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->
    <Assembly Dynamic="Required All" Name="*Application*"/>
    <!-- Add your application specific runtime directives here. -->
    </Application></Directives>
    ```

4. Öffnen Sie die Projektmappe, die Ihre vorhandene Windows Store 8.1-App oder Windows Phone 8.1-App enthält, in Visual Studio.

5. Klicken Sie mit der rechten Maustaste auf das vorhandene Projekt für Ihre App im Projektmappen-Explorer, und wählen Sie dann **Projekt entladen**aus. Nachdem das Projekt entladen wurde, klicken Sie mit der rechten Maustaste erneut auf die Projektdatei, und wählen Sie die Option zum Bearbeiten der CSPROJ- oder VBPROJ-Datei.

     ![Mit der rechten Maustaste auf das Projekt klicken und die Option zum Bearbeiten auswählen](../misc/media/uap-editproject.png "UAP_EditProject")

6. Suchen Sie das- \<PropertyGroup> Element, das das- \<TargetPlatformVersion> Element mit dem Wert 8,1 enthält. Führen Sie für dieses Element die folgenden Schritte aus \<PropertyGroup> :

    1. Legen Sie den Wert des- \<Platform> Elements auf **x86**fest.

    2. Fügen Sie ein \<TargetPlatformIdentifier> -Element hinzu, und legen Sie dessen Wert auf **UAP**fest.

    3. Ändern Sie den vorhandenen Wert des- \<TargetPlatformVersion> Elements in den Wert der universelle Windows-Plattform Version, die Sie installiert haben. Fügen Sie auch ein \<TargetPlatformMinVersion> -Element hinzu, und geben Sie ihm denselben Wert.

    4. Ändern Sie den Wert des- \<MinimumVisualStudioVersion> Elements in: **14**.

    5. Ersetzen Sie das- \<ProjectTypeGuids> Element wie unten dargestellt:

         Für C#:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         Für VB:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. Fügen Sie ein \<EnableDotNetNativeCompatibleProfile> -Element hinzu, und legen Sie dessen Wert auf **true**fest.

    7. Die standardmäßige Objektskalierung für universelle Windows-Apps liegt bei 200. Wenn das Projektressourcen enthält, die nicht bei 200 skaliert sind, müssen Sie \<UapDefaultAssetScale> dieser PropertyGroup ein-Element mit dem Wert der Skala Ihrer Assets hinzufügen. Erfahren Sie mehr mehr über [Objekte und Skalierungen](https://msdn.microsoft.com/library/jj679352.aspx).

         \<PropertyGroup>Das Element sollte nun in etwa wie in diesem Beispiel aussehen:

        ```xml
        <PropertyGroup>
            …
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

7. Ersetzen Sie alle Instanzen von 12.0 durch 14.0 entsprechend der Version von Visual Studio, die Sie derzeit verwenden. Wie diese Instanzen:

    ```xml
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

    ```
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">
        <VisualStudioVersion>14.0</VisualStudioVersion>
    ```

8. Suchen Sie \<PropertyGroup> Elemente, die für die anycpu-Plattform als Teil des Condition-Attributs konfiguriert sind. Entfernen Sie diese Elemente und alle ihre untergeordneten Elemente. AnyCPU wird für Windows 10-Apps in Visual Studio 2015 nicht unterstützt. Sie sollten z. b. \<PropertyGroup> Elemente wie diese entfernen:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
    ```

9. Überprüfen Sie für jedes verbleibende \<PropertyGroup> Element, ob das Element über ein Condition-Attribut mit einer Releasekonfiguration verfügt. Wenn dies der Fall ist, aber kein- \<UseDotNetNativeToolchain> Element enthalten ist, fügen Sie ein-Element hinzu. Legen Sie den Wert für das- \<UseDotNetNativeToolchain> Element wie folgt auf true fest:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">
        <OutputPath>bin\x64\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <Optimize>true</Optimize>
        <NoWarn>;2008</NoWarn>
        <DebugType>pdbonly</DebugType>
        <PlatformTarget>x64</PlatformTarget>
        <UseVSHostingProcess>false</UseVSHostingProcess>
        <ErrorReport>prompt</ErrorReport>
        <Prefer32Bit>true</Prefer32Bit>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

10. Entfernen Sie nur bei Windows Phone Projekten das- \<PropertyGroup> Element, das ein- \<TargetPlatformIdentifier> Element mit einem Wert von windowsphoneapp enthält. Entfernen Sie zudem alle untergeordneten Elemente dieses Elements:

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. Suchen Sie das- \<ItemGroup> Element, das das- \<AppxManifest> Element enthält. Fügen Sie das folgende-Element als untergeordnetes Element \<None> des- \<ItemGroup> Elements hinzu:

    ```xml
    <None Include="project.json" />
    ```

12. Suchen Sie das- \<ItemGroup> Element, das andere Ressourcen enthält, die dem Projekt hinzugefügt werden, z. b. Logo. png-Dateien ( \<Content Include="Assets\Logo.scale-100.png" /> ). Fügen Sie das folgende untergeordnete \<Content> Element zu diesem \<ItemGroup> Element hinzu:

     **Für C#:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **Für VB:**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. Suchen \<ItemGroup> Sie nach dem-Element, das \<Reference> untergeordnete Elemente für nuget-Pakete enthält. Notieren Sie sich die NuGet-Pakete, die Sie verwenden, da Sie sie mit dem NuGet-Paket-Manager herunterladen müssen, nachdem Ihr Projekt erneut geladen wurde. Entfernen Sie dies \<ItemGroup> zusammen mit den zugehörigen untergeordneten Elementen. Beispielsweise könnte ein UWP-Projekt die folgenden NuGet-Pakete aufweisen, die entfernt werden müssten:

    ```xml
    <ItemGroup>
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
          <Private>True</Private>
        </Reference>
      </ItemGroup>
    ```

14. Speichern Sie die Änderungen.

15. Schließen Sie die CSPROJ- oder VBPROJ-Datei.

16. Klicken Sie mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer, und wählen Sie im Kontextmenü „Projekt erneut laden“. Alle Dateien im Projekt sollten nun im Projektmappen-Explorer angezeigt werden.

17. Verwenden Sie den NuGet-Manager, um die von Ihnen in einem früheren Schritt gelöschten Pakete erneut hinzuzufügen.

     Nun müssen Sie die Schritte befolgen, um die [Paketmanifestdateien für alle Ihre Windows Store 8.1- oder Windows Phone 8.1-Projekte zu aktualisieren](#PackageManifest) .

## <a name="migrate-your-c-windows-store-81-or-windows-phone-81-apps-to-use-the-universal-windows-platform"></a><a name="MigrateCPlusPlus"></a> Migrieren Sie Ihre C++ Windows Store 8,1-oder Windows Phone 8,1-apps, um die universelle Windows-Plattform

#### <a name="migrate-your-c-project-files"></a>Migrieren Ihrer C++-Projektdateien

1. Um zu erfahren, welche universelle Windows-Plattform installiert ist, öffnen Sie diesen Ordner: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Er enthält eine Liste der Ordner für jede universelle Windows-Plattform, die installiert ist. Der Ordnername ist die Version der universellen Windows-Plattform, die installiert ist. Auf diesem Windows 10-Gerät beispielsweise ist die Version 10.0.10240.0 der universellen Windows-Plattform installiert.

     ![Den Ordner öffnen, um die installierten Versionen anzuzeigen](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Es kann mehr als eine Version der universellen Windows-Plattform installiert sein. Es wird empfohlen, dass Sie die neueste Version für Ihre App verwenden.

2. Öffnen Sie die Projektmappe, die Ihre vorhandene C++-Windows Store 8.1-App oder -Windows Phone 8.1-App in Visual Studio enthält.

     Klicken Sie mit der rechten Maustaste auf das vorhandene Projekts im Projektmappen-Explorer, und wählen Sie dann **Projekt entladen**. Nachdem das Projekt entladen wurde, klicken Sie mit der rechten Maustaste erneut auf die Projektdatei, und wählen Sie die Option zum Bearbeiten der VCXPROJ-Datei.

     ![Klicken Sie mit der rechten&#45;auf Projektdatei und dann auf Bearbeiten.](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. Suchen Sie das- \<PropertyGroup> Element, das das- \<ApplicationTypeRevision> Element mit dem Wert 8,1 enthält. Führen Sie für dieses Element die folgenden Schritte aus \<PropertyGroup> :

    1. Fügen \<WindowsTargetPlatformVersion> Sie ein-Element und ein \<WindowsTargetPlatformMinVersion> -Element hinzu, und geben Sie ihm den Wert der universelle Windows-Plattform Version, die Sie installiert haben.

    2. Aktualisieren Sie den Wert des Elements „ApplicationTypeRevision“ von „8.1“auf „10.0“.

    3. Ändern Sie den Wert des- \<MinimumVisualStudioVersion> Elements in: 14.

    4. Fügen Sie ein \<EnableDotNetNativeCompatibleProfile> -Element hinzu, und legen Sie dessen Wert auf true fest.

    5. Die standardmäßige Objektskalierung für universelle Windows-Apps liegt bei 200. Wenn das Projektressourcen enthält, die nicht bei 200 skaliert sind, müssen Sie \<UapDefaultAssetScale> dieser PropertyGroup ein-Element mit dem Wert der Skala Ihrer Assets hinzufügen. Erfahren Sie mehr mehr über [Objekte und Skalierungen](https://msdn.microsoft.com/library/jj679352.aspx).

    6. Ändern Sie für Windows Phone-Projekte den Wert von \<ApplicationType> von Windows phone in den Windows Store.

         \<PropertyGroup>Das Element sollte nun in etwa wie in diesem Beispiel aussehen:

        ```xml
        <PropertyGroup>
            …
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
             <ApplicationType>Windows Store</ApplicationType>
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

4. Ändern Sie alle Instanzen des \<PlatformToolset> Elements so, dass Sie den Wert V140 haben. Beispiel:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. Überprüfen Sie für jedes verbleibende \<PropertyGroup> Element, ob das Element über ein Condition-Attribut mit einer Releasekonfiguration verfügt. Wenn dies der Fall ist, aber kein- \<UseDotNetNativeToolchain> Element enthalten ist, fügen Sie ein-Element hinzu. Legen Sie den Wert für das- \<UseDotNetNativeToolchain> Element wie folgt auf true fest:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

6. Speichern Sie die Änderungen. Schließen Sie dann die Projektdatei.

7. Klicken Sie mit der rechten Maustaste auf die Projektdatei im Projektmappen-Explorer, und wählen Sie im Kontextmenü „Projekt erneut laden“. Alle Dateien im Projekt sollten nun im Projektmappen-Explorer angezeigt werden.

     Nun müssen Sie die Schritte befolgen, um die [Paketmanifestdateien für alle Ihre Windows Store 8.1- oder Windows Phone 8.1-Projekte zu aktualisieren](#PackageManifest) .

## <a name="update-your-package-manifest-file-for-all-your-windows-store-81-or-windows-phone-81-projects"></a><a name="PackageManifest"></a> Aktualisieren Sie die Paket Manifest-Datei für alle Windows Store 8,1-oder Windows Phone 8,1-Projekte.
 Sie müssen die Paketmanifestdatei für jedes Projekt in der Projektmappe aktualisieren.

#### <a name="update-your-package-manifest-file"></a>Aktualisieren der Paketmanifestdatei

1. Öffnen Sie die Datei „Package.appxmanifest“ im Projektmappen-Explorer. Sie müssen die Datei „Package.AppxManifest“ für jedes Windows Store- und Windows Phone-Projekt bearbeiten.

2. Sie müssen das- \<Package> Element mit den neuen Schemas aktualisieren, basierend auf dem vorhandenen Projekttyp. Entfernen Sie zuerst die folgenden Schemas, je nachdem, ob Sie über ein Windows Store- oder ein Windows Phone-Projekt verfügen.

    **Altes für Windows Store-Projekt:** \<Package> Das Element sieht in etwa wie folgt aus.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **Alt für Windows Phone Projekt:** \<Package> Das Element sieht in etwa wie folgt aus.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **Neu für universelle Windows-Plattform:** Fügen Sie dem-Element die unten aufgeführten Schemas hinzu \<Package> . Entfernen Sie alle zugehörigen Namespace-Bezeichnerpräfixe von Elementen für die Schemas, die Sie gerade entfernt haben. Aktualisieren Sie die IgnorableNamespaces-Eigenschaft auf „uap mp“. Das neue \<Package> Element sollte in etwa wie folgt aussehen.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. Fügen Sie \<Dependencies> dem-Element ein untergeordnetes-Element hinzu \<Package> . Fügen Sie diesem Element dann ein untergeordnetes \<TargetDeviceFamily> Element \<Dependencies> mit den Attributen Name, MinVersion und maxversiongetesteten hinzu. Weisen Sie dem Name-Attribut den Wert „Windows.Universal“ zu. Geben Sie „MinVersion“ und „MaxVersionTested“ den Wert der installierten Version der universellen Windows-Plattform. Dieses Element sollte in etwa wie folgt aussehen:

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **Nur für Windows Store:** Sie müssen dem-Element ein untergeordnetes-Element hinzufügen \<mp:PhoneIdentity> \<Package> . Fügen Sie ein „PhoneProductId“-Attribut und ein „PhonePublisherId“-Attribut hinzu. Legen Sie die phoneproductid so fest, dass Sie denselben Wert wie das Name-Attribut im- \<Identity> Element hat. Legen Sie den „PhonePublishedId“-Wert auf Folgendes fest: 00000000-0000-0000-0000-000000000000. Und zwar so:

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. Suchen Sie das- \<Prerequisites> Element, und löschen Sie dieses Element und alle untergeordneten Elemente, die es besitzt.

6. Fügen Sie den **UAP** -Namespace zu den folgenden \<Resource> Elementen hinzu: Scale, dxfeaturelevel. Beispiel:

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. Fügen Sie den **UAP** -Namespace zu den folgenden \<Capability> Elementen hinzu: documentslibrary, pictureslibrary, videoslibrary, musiclibrary, enterprisauthentication, shareduserzertifikate, removablestorage, Termine und Kontakte. Beispiel:

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. Fügen Sie dem-Element und seinen untergeordneten Elementen den **UAP** -Namespace hinzu \<VisualElements> . Beispiel:

   ```xml
   <uap:VisualElements
       DisplayName="My WWA App"
       Square150x150Logo="images/150x150.png"
       Square44x44Logo="images/44x44.png"
       Description="My WWA App"
       BackgroundColor="#777777">
     <uap:SplashScreen Image="images/splash.png"/>
   </uap:VisualElements>

   ```

    **Gilt nur für Windows Store:** Die Namen der Kachelgröße wurden geändert. Ändern Sie die Attribute im- \<VisualElements> Element, um die neuen konvergierten Kachel Größen widerzuspiegeln. 70 x 70 wird zu 71 x 71 und 30 x 30 zu 44 x 44.

    **ALT:** Kachelgrößennamen

   ```xml
   <m2:VisualElements
       …
       Square30x30Logo="Assets\SmallLogo.png"
       …>
    <m2:DefaultTile
         …
         Square70x70Logo="images/70x70.png">
   </m2:VisualElements>

   ```

    **NEU:** Kachelgrößennamen

   ```xml
   <uap:VisualElements
       …
       Square44x44Logo="Assets\SmallLogo.png"
       …>
    <uap:DefaultTile
         …
         Square71x71Logo="images/70x70.png">
   </uap:VisualElements>

   ```

9. Fügen Sie den **UAP** -Namespace zu \<ApplicationContentUriRules> und allen untergeordneten Elementen hinzu. Beispiel:

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. Fügen Sie den **UAP** -Namespace zu den folgenden \<Extension> Elementen und allen untergeordneten Elementen hinzu: Windows. accountpictureprovider, Windows. Alarm, Windows.. autoplaycontent, Windows. autoplaydevice, Windows. cachedfileupdate, Windows. camerasettings, Windows. fileopenpicker, Windows. filetypeassociation, Windows. filesavepicke, Windows. lockscreencall, Windows. printtasksettings, Windows. Protocol, Windows. Search, Windows. sharetarget. Beispiel:

    ```xml
    <Extensions>
      <uap:Extension Category="windows.alarm"/>
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>
      <uap:Extension Category="windows.protocol">
        <uap:Protocol Name="mailto" DesiredView="useHalf">
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>
        </uap:Protocol>
      </uap:Extension>
    </Extensions>

    ```

11. Fügen Sie den **uap** -Namespace zu Hintergrundaufgaben des Typs „chatMessageNotification“ hinzu. Beispiel:

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
     <BackgroundTasks ServerName="MyBackgroundTasks">
        <uap:Task Type="chatMessageNotification"/>
      </BackgroundTasks>
    </Extension>

    ```

12. Ändern Sie die Framework-Abhängigkeiten. Fügen Sie allen Elementen einen Herausgeber Namen hinzu \<PackageDependency> , und geben Sie eine MinVersion an, wenn Sie nicht bereits angegeben ist.

     **Alt:** \<PackageDependency> gewisses

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **Neu:** \<PackageDependency> gewisses

    ```xml
    <Dependencies>
     <PackageDependency
          Name="Microsoft.VCLibs.120.00"
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
          MinVersion="12.0.30113.0" />
    </Dependencies>

    ```

     Verwenden Sie die entsprechenden Werte für „Publisher“ und „MinVersion“ für das tatsächlich verwendete Framework. Beachten Sie, dass sich diese Namen für Windows 10 ändern können.

13. Ersetzen Sie die Hintergrundaufgaben „gattCharacteristicNotification“ und „rfcommConnection“ durch eine Aufgabe vom Typ Bluetooth. Beispiel:

     **Jährigen**

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
                <Task Type="rfcommConnection"/>
               <Task Type="gattCharacteristicNotification"/>
    </BackgroundTasks>
    </Extension>
    ```

     **NEU:** Mit der Aufgabe vom Typ Bluetooth.

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
               <Task Type="bluetooth"/>
    </BackgroundTasks>
    </Extension>
    ```

14. Ersetzen Sie die Bluetooth-Gerätefunktionen „bluetooth.rfcomm“ und „bluetooth.genericAttributeProfile“ durch eine generische Bluetooth-Funktion. Beispiel:

     **Jährigen**

    ```xml
    <Capabilities>
      <m2:DeviceCapability Name="bluetooth.rfcomm">
        <m2:Device Id="any">
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>
        </m2:Device>
      </m2:DeviceCapability>
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">
        <m2:Device Id="any">
         <m2:Function Type="name:heartRate"/>
        </m2:Device>
      </m2:DeviceCapability>
    </Capabilities>
    ```

     **NEU:** Ersetzt durch eine generische Bluetooth-Funktion.

    ```xml
    <Capabilities>
      <uap:DeviceCapability Name="bluetooth"/>
    </Capabilities>

    ```

15. Entfernen Sie alle veralteten Elemente.

    1. Diese Attribute für \<VisualElements> sind veraltet und sollten entfernt werden:

       - Die \<VisualElements> Attribute: foregroundtext, toastfähig

       - Das \<DefaultTile> Attribut "DefaultSize"

       - Das \<ApplicationView>-Element

         Beispiel:

       ```xml
       <m2:VisualElements
           …
           ForegroundText="dark"
           ToastCapable="true">
       <m2:DefaultTile DefaultSize="square150x150Logo"/>
         <m2:ApplicationView MinWidth="width320"/>
       </m2:VisualElements>

       ```

    2. Entfernen Sie die Erweiterungen „Windows.contact“ und „windows.contactPicker“ und alle Elemente unter diesen Erweiterungen.

16. Speichern Sie die Datei „Package.appxmanifest“. Schließen Sie dann Visual Studio.

17. Sie müssen einige ausgeblendete Dateien entfernen, bevor Sie die Projektmappe erneut öffnen können.

    1. Öffnen Sie den Datei-Explorer, klicken Sie in der Symbolleiste auf **Ansicht** , und wählen Sie **Ausgeblendete Elemente** und **Dateinamenerweiterungen**. Öffnen Sie diesen Ordner auf Ihrem Computer: \<path for the location of your solution> \\ . vs \\ {Project Name} \v14. Wenn eine Datei mit der Erweiterung .suo vorhanden ist, löschen Sie sie.

    2. Kehren Sie nun zurück zu dem Ordner, in dem sich die Projektmappe befindet. Öffnen Sie Ordner für Projekte, die in der Projektmappe vorhanden sind. Wenn eine Datei innerhalb eines dieser Projektordner über eine Erweiterung „.csproj.user“ oder „.vbproj.user“ verfügt, löschen Sie sie.

         Sie können Ihre Projektmappe nun wieder in Visual Studio öffnen. Sie können Ihre App nun mithilfe der universellen Windows-Plattform codieren, erstellen und debuggen.

         Erfahren Sie, wie Sie [Ihren Code anpassen können](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) , um die neuen Funktionen der universellen Windows-Plattform nutzen zu können.

## <a name="changes-required-for-existing-universal-windows-apps-created-with-visual-studio-2015-rc"></a><a name="PreviousVersions"></a> Erforderliche Änderungen für vorhandene universelle Windows-apps, die mit Visual Studio 2015 RC erstellt wurden
 Wenn Sie universelle Windows 10-Apps mit Visual Studio 2015 RC erstellt haben, müssen Sie Ihr Projekt neu ausrichten, um die Version der UWP zu verwenden, die mit der neuesten Version von Visual Studio 2015 installiert wurde. Vorherige Versionen werden nicht unterstützt. Die erforderlichen Änderungen unterscheiden sich abhängig von der Sprache, die Sie zum Erstellen der App verwendet haben:

- [C#/VB-Apps](#RCUpdate10CSharp)

- [C++-apps](#RCUpdate10CPlusPlus)

### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a><a name="RCUpdate10CSharp"></a> Aktualisieren Ihrer c#-/VB-Projekte zur Verwendung der neuesten universelle Windows-Plattform
 Wenn Sie Ihre Projektmappe für Ihre vorhandene App öffnen, sehen Sie, dass für Ihre App eine Aktualisierung erforderlich ist:

 ![Anzeigen der Projektmappe im Projektmappen-Explorer.](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 Wenn Sie das Projekt über den Projektmappen-Explorer erneut laden, wird dieses Dialogfeld angezeigt:

 ![Nehmen Sie eine Neuzuordnung vor, und weisen Sie Ihrer App das richtige SDK zu.](../misc/media/missingsdkforuap.png "Missingsdkforuap")

 Da das universelle Windows-Plattform-SDK für Ihr Projekt nun nicht unterstützt wird, können Sie es nicht installieren. Klicken Sie auf „OK“, und befolgen Sie dann die folgenden Schritte.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Aktualisieren der C#/VB-Projekte zur Verwendung der neuesten universellen Windows-Plattform

1. Um zu erfahren, welche universelle Windows-Plattform installiert ist, öffnen Sie diesen Ordner: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Er enthält eine Liste der Ordner für jede universelle Windows-Plattform, die installiert ist. Der Ordnername ist die Version der universellen Windows-Plattform, die installiert ist. Auf diesem Windows 10-Gerät beispielsweise ist die Version 10.0.10240.0 der universellen Windows-Plattform installiert.

    ![Den Ordner öffnen, um die installierten Versionen anzuzeigen](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

    Es kann mehr als eine Version der universellen Windows-Plattform installiert sein. Es wird empfohlen, dass Sie die neueste Version für Ihre App verwenden.

2. Wechseln Sie mithilfe des Datei-Explorers zum Ordner, in dem Ihr UWP-Projekt gespeichert ist. Löschen Sie die Datei „packages.config“, und erstellen Sie eine neue JSON-Datei in diesem Ordner. Benennen Sie die Datei „project.json“, und fügen Sie der Datei anschließend den folgenden Inhalt hinzu:

   ```json

   {
     "dependencies": {
       "Microsoft.ApplicationInsights": "1.0.0",
       "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
       "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
       "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
     },
     "frameworks": {
       "uap10.0": {}
     },
     "runtimes": {
       "win10-arm": {},
       "win10-arm-aot": {},
       "win10-x86": {},
       "win10-x86-aot": {},
       "win10-x64": {},
       "win10-x64-aot": {}
     }
   }

   ```

3. Öffnen Sie unter Verwendung von Visual Studio Ihre Projektmappe, die Ihre universelle C#-/VB-Windows-App enthält. Sie sehen, dass die Projektdatei (CSPROJ- oder VBPROJ-Datei) aktualisiert werden muss. Klicken Sie mit der rechten Maustaste auf die Projektdatei, und wählen Sie die Option zum Bearbeiten der Datei.

    ![Mit der rechten Maustaste auf das Projekt klicken und die Option zum Bearbeiten auswählen](../misc/media/uap-editproject.png "UAP_EditProject")

4. Suchen Sie das \<PropertyGroup> -Element, das die \<TargetPlatformVersion> -und- \<TargetPlatformMinVersion> Elemente enthält. Ändern Sie den vorhandenen Wert des \<TargetPlatformVersion> -Elements und des- \<TargetPlatformMinVersion> Elements in die gleiche Version der universelle Windows-Plattform, die Sie installiert haben.

    Die standardmäßige Objektskalierung für universelle Windows-Apps liegt bei 200. Projekte, die mit Visual Studio 2015 RC erstellt wurden, enthalten Ressourcen, die auf 100 skaliert werden. Sie müssen \<UapDefaultAssetScale> dieser PropertyGroup ein-Element mit dem Wert 100 hinzufügen. Erfahren Sie mehr mehr über [Objekte und Skalierungen](https://msdn.microsoft.com/library/jj679352.aspx).

5. Wenn Sie Verweise zu den SDKs für die UWP-Erweiterung (wie das Windows Mobile SDK) hinzugefügt haben, müssen Sie die SDK-Version aktualisieren. Beispiel für dieses \<SDKReference> Element:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

    sollte wie folgt geändert werden:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

6. Suchen Sie das- \<Target> Element mit einem Name-Attribut, das den Wert "ensurenugetpackagebuildimports" hat. Löschen Sie dieses Element und alle zugehörigen untergeordneten Elemente.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. Suchen und löschen Sie die \<Import> Elemente mit Project-und Condition-Attributen, die auf "Microsoft. Diagnostics. Tracing. eventSource" und "Microsoft. applicationinsights" folgendermaßen verweisen:

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. Suchen \<ItemGroup> Sie nach der, die \<Reference> untergeordnete Elemente für nuget-Pakete enthält. Notieren Sie sich die NuGet-Pakete, die referenziert wurden, da Sie diese Informationen in einem künftigen Schritt benötigen. Ein entscheidender Unterschied zwischen dem Windows 10-Projektformat zwischen Visual Studio 2015 RC und Visual Studio 2015 RTM besteht darin, dass das RTM-Format [NuGet](/nuget/) Version 3 verwendet.

    Entfernen Sie und alle zugehörigen untergeordneten Elemente \<ItemGroup> . Beispielsweise weist ein mit Visual Studio RC erstelltes UWP-Projekt die folgenden zu löschenden NuGet-Pakete auf:

   ```xml
   <ItemGroup>
       <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
         <Private>True</Private>
       </Reference>
     </ItemGroup>

   ```

9. Suchen Sie das- \<ItemGroup> Element, das ein- \<AppxManifest> Element enthält. Wenn ein- \<None> Element mit einem Include-Attribut auf festgelegt ist: packages.config, löschen Sie es. Fügen Sie außerdem ein \<None> -Element mit einem Include-Attribut hinzu, und legen Sie dessen Wert auf fest: project.json.

10. Speichern Sie die Änderungen. Schließen Sie dann die Projektdatei.

11. Klicken Sie mit der rechten Maustaste auf die Projektdatei im Projektmappen-Explorer, und wählen Sie im Kontextmenü „Projekt erneut laden“. Alle Dateien im Projekt sollten nun im Projektmappen-Explorer angezeigt werden.

12. Wählen Sie die Datei „ApplicationInsights.config“ im Projektmappen-Explorer aus, und öffnen Sie die zugehörigen Eigenschaften. Legen Sie die Eigenschaft für die Buildaktion auf „Content“ fest, und kopieren Sie die Eigenschaft für das Ausgabeverzeichnis zu „Kopieren, wenn neuer“.

13. Öffnen Sie die Datei „Package.appxmanifest“ im Projektmappen-Explorer.

    1. Suchen Sie das \<TargetDeviceFamily> -Element. Ändern Sie die zugehörigen Attribute „MinVersion“ und „MaxVersionTested“ auf die installierte Version der universellen Windows-Plattform. Und zwar so:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Speichern Sie die Änderungen.

14. Verwenden Sie den NuGet-Manager zum Hinzufügen der Pakete, die Sie im vorherigen Schritt gelöscht haben. Ein entscheidender Unterschied zwischen dem Windows 10-Projektformat zwischen Visual Studio 2015 RC und Visual Studio 2015 RTM besteht darin, dass das RTM-Format [NuGet](/nuget/) Version 3 verwendet.

    Sie können Ihre App nun codieren, erstellen und debuggen.

    Wenn Sie über Komponententestprojekte für Ihre universellen Windows-Apps verfügen, müssen Sie zudem die [diese Schritte](#MigrateUnitTest)befolgen.

### <a name="update-your-c-projects-to-use-the-latest-universal-windows-platform"></a><a name="RCUpdate10CPlusPlus"></a> Aktualisieren der C++-Projekte zur Verwendung der neuesten universelle Windows-Plattform

1. Um zu erfahren, welche universelle Windows-Plattform installiert ist, öffnen Sie diesen Ordner: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Er enthält eine Liste der Ordner für jede universelle Windows-Plattform, die installiert ist. Der Ordnername ist die Version der universellen Windows-Plattform, die installiert ist. Auf diesem Windows 10-Gerät beispielsweise ist die Version 10.0.10240.0 der universellen Windows-Plattform installiert.

     ![Den Ordner öffnen, um die installierten Versionen anzuzeigen](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Es kann mehr als eine Version der universellen Windows-Plattform installiert sein. Es wird empfohlen, dass Sie die neueste Version für Ihre App verwenden.

2. Öffnen Sie die Projektmappe, die die universelle C++-Windows-App enthält. Klicken Sie mit der rechten Maustaste auf die VCXPROJ-Datei des Projekts, und wählen Sie die Option zum Entladen der Projektdatei. Nachdem das Projekt entladen wurde, klicken Sie mit der rechten Maustaste erneut auf die Projektdatei, und wählen Sie die Option zum Bearbeiten.

     ![Das Projekt entladen und dann die Projektdatei bearbeiten](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. Suchen Sie \<PropertyGroup> Elemente, die kein Condition-Attribut enthalten, aber ein- \<ApplicationTypeRevision> Element enthalten. Aktualisieren Sie den Wert für „ApplicationTypeRevision“ von „8.2“ auf „10.0“. Fügen Sie ein \<WindowsTargetPlatformVersion> -Element und ein- \<WindowsTargetPlatformMinVersion> Element hinzu, und legen Sie deren Werte auf den Wert der universelle Windows-Plattform Version fest, die Sie installiert haben.

     Fügen Sie ein \<EnableDotNetNativeCompatibleProfile> Element hinzu, und legen Sie dessen Wert auf true fest, wenn das Element nicht bereits vorhanden ist.

     Die standardmäßige Objektskalierung für universelle Windows-Apps liegt bei 200. Projekte, die mit Visual Studio 2015 RC erstellt wurden, enthalten Ressourcen, die auf 100 skaliert werden. Sie müssen \<UapDefaultAssetScale> dieser PropertyGroup ein-Element mit dem Wert 100 hinzufügen. Erfahren Sie mehr mehr über [Objekte und Skalierungen](https://msdn.microsoft.com/library/jj679352.aspx).

     Dieses \<PropertyGroup> Element sieht nun in etwa wie folgt aus:

    ```xml
    <PropertyGroup Label="Globals">
        …
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>
        <ApplicationType>Windows Store</ApplicationType>
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
        <UapDefaultAssetScale>100</UapDefaultAssetScale>
      </PropertyGroup>

    ```

4. Überprüfen Sie für jedes verbleibende \<PropertyGroup> Element, ob das Element über ein Condition-Attribut mit einer Releasekonfiguration verfügt. Wenn dies der Fall ist, aber kein- \<UseDotNetNativeToolchain> Element enthalten ist, fügen Sie ein-Element hinzu. Legen Sie den Wert für das- \<UseDotNetNativeToolchain> Element wie folgt auf true fest:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. Sie müssen das \<EnableDotNetNativeCompatibleProfile> -Element und das- \<UseDotNetNativeToolchain> Element aktualisieren, um .net Native zu aktivieren, aber .net Native ist nicht in den C++-Vorlagen aktiviert.

     Speichern Sie die Änderungen. Schließen Sie dann die Projektdatei.

6. Klicken Sie mit der rechten Maustaste auf die Projektdatei im Projektmappen-Explorer, und wählen Sie im Kontextmenü „Projekt erneut laden“. Alle Dateien im Projekt sollten nun im Projektmappen-Explorer angezeigt werden.

7. Öffnen Sie die Datei „Package.appxmanifest“ im Projektmappen-Explorer.

    1. Suchen Sie das \<TargetDeviceFamily> -Element. Ändern Sie die zugehörigen Attribute „MinVersion“ und „MaxVersionTested“ auf die installierte Version der universellen Windows-Plattform. Und zwar so:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Speichern Sie die Änderungen.

         Sie können Ihre App nun codieren, erstellen und debuggen.

         Wenn Sie über Komponententestprojekte für Ihre universellen Windows-Apps verfügen, müssen Sie zudem die [diese Schritte](#MigrateUnitTest)befolgen.

## <a name="changes-required-for-existing-unit-test-projects-for-universal-windows-apps-created-with-visual-studio-2015-rc"></a><a name="MigrateUnitTest"></a> Erforderliche Änderungen für vorhandene Komponenten Testprojekte für universelle Windows-apps, die mit Visual Studio 2015 RC erstellt wurden
 Wenn Sie Komponententestprojekte für universelle Windows 10-Apps mit Visual Studio 2015 RC erstellt haben, müssen Sie diese zusätzlichen Änderungen an Ihren Projektdateien vornehmen, um diese Testprojekte mit der neuesten Version von Visual Studio 2015 verwenden zu können. Die erforderlichen Änderungen unterscheiden sich abhängig von der Sprache, die Sie zum Erstellen der App verwendet haben:

- [C#/VB-Apps](#UnitTestRCUpdate10CSharp)

- [C++-apps](#UnitTestRCUpdate10CPlusPlus)

### <a name="update-your-cvb-unit-test-projects"></a><a name="UnitTestRCUpdate10CSharp"></a> Aktualisieren Ihrer c#-/VB-Komponenten Testprojekte

1. Öffnen Sie unter Verwendung von Visual Studio Ihre Projektmappe, die Ihr C#-/VB-Komponententestprojekt enthält. Ändern Sie den Wert des- \<OuttputType> Elements in: appcontainerexe.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Ersetzen Sie dieses \<EnableCoreRuntime> Element \</EnableCoreRuntime> mit dem folgenden Element false:

   ```xml

   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>

   ```

3. Entfernen Sie die folgenden Zeilen:

   ```xml

   <PropertyGroup>
       <AppXPackage>True</AppXPackage>
       <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
       <PlatformTarget>AnyCPU</PlatformTarget>
       <DebugType>pdbonly</DebugType>
       <Optimize>true</Optimize>
       <OutputPath>bin\Release\</OutputPath>
       <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
       <ErrorReport>prompt</ErrorReport>
       <WarningLevel>4</WarningLevel>
    </PropertyGroup>

   ```

4. Fügen Sie dieses Element " \<UseDotNetNativeToolchain> true" \</UseDotNetNativeToolchain> als untergeordnetes Element zu diesen Eigenschaften Gruppen hinzu:

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Löschen Sie die folgenden \<ItemGroup> Elemente:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="packages.config" />
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\Default.rd.xml" />
      <Content Include="Assets\Logo.scale-240.png" />
      <Content Include="Assets\SmallLogo.scale-240.png" />
      <Content Include="Assets\SplashScreen.scale-240.png" />
      <Content Include="Assets\Square71x71Logo.scale-240.png" />
      <Content Include="Assets\StoreLogo.scale-240.png" />
      <Content Include="Assets\WideLogo.scale-240.png" />
   </ItemGroup>

   ```

    Ersetzen Sie sie durch die folgenden Elemente:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTestApp.xaml.cs">
         <DependentUpon>UnitTestApp.xaml</DependentUpon>
      </Compile>
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <ApplicationDefinition Include="UnitTestApp.xaml">
         <Generator>MSBuild:Compile</Generator>
         <SubType>Designer</SubType>
      </ApplicationDefinition>
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\UnitTestApp.rd.xml" />
      <Content Include="Assets\LockScreenLogo.scale-200.png" />
      <Content Include="Assets\SplashScreen.scale-200.png" />
      <Content Include="Assets\Square150x150Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
      <Content Include="Assets\StoreLogo.png" />
      <Content Include="Assets\Wide310x150Logo.scale-200.png" />
   </ItemGroup>
   ```

6. Erstellen Sie ein neues Komponententestprojekt, und kopieren Sie die Dateien „UnitTestApp.xaml“ und „UnitTestApp.xaml.cs“ aus dem neuen Projekt zum vorhandenen Komponententestprojekt, welches Sie aktualisieren.

7. Kopieren Sie die Datei „UnitTestApp.rd.xml“ aus dem Eigenschaftsordner des neuen Komponententestprojekts zum Eigenschaftsordner des vorhandenen Komponententestprojekts, welches Sie aktualisieren.

8. Öffnen Sie die Datei „Package.appxmanifest“ im Projektmappen-Explorer. Löschen Sie anschließen diese Elemente daraus:

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="vstest.executionengine.appcontainer.uap.exe"
            EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
         <uap:VisualElements
            DisplayName="UnitTestProject1"
            Square150x150Logo="Assets\Logo.png"
            Square44x44Logo="Assets\SmallLogo.png"
            Description="UnitTestProject1"
            BackgroundColor="#464646">
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClientServer" />
   </Capabilities>
   ```

    Ersetzen Sie diese gelöschten Elemente durch die folgenden Elemente. Verwenden Sie den entsprechenden Wert für „ProjectName“ auf Grundlage des Namens Ihres Projekts und nicht „UnitTestProject1“ in den unten aufgeführten Elementen.

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="$targetnametoken$.exe"
            EntryPoint="UnitTestProject1.App">
         <uap:VisualElements
               DisplayName="UnitTestProject1"
               Square150x150Logo="Assets\Square150x150Logo.png"
               Square44x44Logo="Assets\Square44x44Logo.png"
               Description="UnitTestProject1"
               BackgroundColor="transparent">
            <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClient" />
   </Capabilities>
   ```

   Sie können nun die Komponententests ausführen.

### <a name="update-your-c-projects-to-use-the-latest-universal-windows-platform"></a><a name="UnitTestRCUpdate10CPlusPlus"></a> Aktualisieren der C++-Projekte zur Verwendung der neuesten universelle Windows-Plattform

1. Öffnen Sie unter Verwendung von Visual Studio Ihre Projektmappe, die Ihr C++-Komponententestprojekt enthält. Entfernen Sie das folgenden Elemente:

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Fügen \<ProjectConfiguration> Sie unterhalb dieses Elements die folgenden Elemente hinzu, \<ItemGroup Label="ProjectConfigurations"> Wenn Sie sich nicht bereits in diesem Filter befinden:

    ```xml

    <ProjectConfiguration Include="Debug|x64">
       <Configuration>Debug</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|x64">
       <Configuration>Release</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>

    ```

3. Ersetzen Sie alle Vorkommen dieses Elements:

    ```xml

    <ConfigurationType>DynamicLibrary</ConfigurationType>

    ```

     durch diesen:

    ```xml

    <ConfigurationType>Application</ConfigurationType>

    ```

4. Fügen Sie diese Elemente hinzu, \<PropertyGroup> Wenn Sie nicht bereits in der Datei vorhanden sind:

    ```xml

    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>true</UseDebugLibraries>
       <PlatformToolset>v140</PlatformToolset>
    </PropertyGroup>
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>false</UseDebugLibraries>
       <WholeProgramOptimization>true</WholeProgramOptimization>
       <PlatformToolset>v140</PlatformToolset>
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
    </PropertyGroup>

    ```

5. Ersetzen Sie alle Vorkommen dieses Elements:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
    ```

     durch diesen:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>

    ```

6. Ersetzen Sie alle Vorkommen dieses Elements:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

     durch diesen:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

7. Fügen Sie diese \<ItemDefinitionGroup> Elemente in dem Abschnitt hinzu, der bereits weitere \<ItemDefinitionGroup> Elemente enthält:

    ```xml

    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
    <Link>
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
    </Link>
    </ItemDefinitionGroup>
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
       <Link>
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
       </Link>
    </ItemDefinitionGroup>

    ```

8. Löschen Sie das folgende \< ItemGroup> Element:

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Ersetzen Sie Sie durch dieses \<ItemGroup> Element:

    ```xml

    <ItemGroup>
       <Image Include="Assets\LockScreenLogo.scale-200.png" />
       <Image Include="Assets\SplashScreen.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
       <Image Include="Assets\Square150x150Logo.scale-200.png" />
       <Image Include="Assets\StoreLogo.png" />
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />
    </ItemGroup>

    ```

9. Löschen Sie das folgende \< ItemGroup> Element:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Ersetzen Sie Sie durch die folgenden \<ItemGroup> Elemente:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
       <ClInclude Include="UnitTestApp.xaml.h">
          <DependentUpon>UnitTestApp.xaml</DependentUpon>
       </ClInclude>
    </ItemGroup>
    <ItemGroup>
       <ApplicationDefinition Include="UnitTestApp.xaml">
          <SubType>Designer</SubType>
       </ApplicationDefinition>
    </ItemGroup>

    ```

10. Löschen Sie das folgende Element:

    ```xml
    <ClCompile Include="UnitTest.cpp"/>
    ```

     Ersetzen Sie Sie durch die folgenden \<CICompile> Elemente:

    ```xml

    <ClCompile Include="UnitTestApp.xaml.cpp">
       <DependentUpon>UnitTestApp.xaml</DependentUpon>
    </ClCompile>
    <ClCompile Include="UnitTest.cpp"/>

    ```

11. Fügen Sie dieses Element hinzu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
    ```

     Über dieses Element in der Datei:

    ```xml

    <ItemGroup>
       <Xml Include="UnitTestApp.rd.xml" />
    </ItemGroup>
    ```

12. Erstellen Sie ein neues C++-Komponententestprojekt, und kopieren Sie die Dateien „UnitTestApp.xaml“, „UnitTestApp.xaml.cpp“, „UnitTestApp.xaml.h“ und „UnitTestApp.rd.xml“ aus diesem Projekt zu Ihrem vorhandenen Projekt, das Sie aktualisieren.

13. Öffnen Sie die Datei „Package.appxmanifest“ im Projektmappen-Explorer. Löschen Sie anschließen diese Elemente daraus:

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
             Executable="vstest.executionengine.appcontainer.uap.exe"
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
          <uap:VisualElements
             DisplayName="UnitTestProject1"
             Square150x150Logo="Assets\Logo.png"
             Square44x44Logo="Assets\SmallLogo.png"
             Description="UnitTestProject1"
             BackgroundColor="#464646">
             <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClientServer" />
    </Capabilities>

    ```

     Ersetzen Sie diese gelöschten Elemente durch die folgenden Elemente. Verwenden Sie den entsprechenden Wert für „ProjectName“ auf Grundlage des Namens Ihres Projekts und nicht „UnitTestProject1“ in den unten aufgeführten Elementen.

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
                Executable="$targetnametoken$.exe"
                EntryPoint="UnitTestProject1.App">
          <uap:VisualElements
                DisplayName="UnitTestProject1"
                Square150x150Logo="Assets\Square150x150Logo.png"
                Square44x44Logo="Assets\Square44x44Logo.png"
                Description="UnitTestProject1"
                BackgroundColor="transparent">
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
                <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClient" />
    </Capabilities>

    ```