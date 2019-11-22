---
title: Migrate apps to the Universal Windows Platform (UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5794aa5ab7dc14932c65a9156ea9252e71731155
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299479"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migrieren von Apps in die universelle Windows-Plattform (UWP)
Nehmen Sie die erforderlichen manuellen Änderungen an Ihren vorhandenen Projektdateien für Windows Store 8.1-Apps, Windows Phone 8.1-Apps oder mit Visual Studio 2015 RC erstellte universelle Windows-Apps vor, damit sie mit Visual Studio 2015 RTM verwendet werden können. (Wenn Sie über eine universelle Windows 8.1-App mit einem Windows-Anwendungsprojekt und einem Windows Phone-Projekt verfügen, müssen Sie die Schritte befolgen, um jedes Projekt zu migrieren).

 Mit der universellen Windows-Plattform können Sie Ihre App auf mindestens eine Gerätefamilie abzielen. Weitere Informationen zu universellen Windows-Apps finden Sie in diesem [Plattform-Handbuch](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

- [Migrieren Sie Ihre vorhandenen C#/VB-Windows Store 8.1- oder -Windows Phone 8.1-Apps](#MigrateCSharp) , um die universelle Windows-Plattform zu verwenden.

- [Migrieren Sie Ihre vorhandenen C++-Windows Store 8.1- oder -Windows Phone 8.1-Apps](#MigrateCPlusPlus) , um die universelle Windows-Plattform zu verwenden.

- [Erforderliche Änderungen für vorhandene mit Visual Studio 2015 RC erstellte universelle Windows-Apps](#PreviousVersions).

- [Erforderliche Änderungen für vorhandene Komponententestprojekte für mit Visual Studio 2015 RC erstellte universelle Windows-Apps](#MigrateUnitTest).

  Wenn Sie diese Änderungen nicht alle vornehmen möchten, erfahren Sie hier mehr über das [Portieren Ihrer vorhandenen Apps](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) in ein neues universelles Windows-Projekt.

## <a name="MigrateCSharp"></a> Migrate your C#/VB Windows Store 8.1 or Windows Phone 8.1 apps to use the Universal Windows Platform

#### <a name="migrate-your-cvb-project-files"></a>Migrieren Ihrer C#/VB-Projektdateien

1. Um zu erfahren, welche universelle Windows-Plattform installiert ist, öffnen Sie diesen Ordner: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Er enthält eine Liste der Ordner für jede universelle Windows-Plattform, die installiert ist. Der Ordnername ist die Version der universellen Windows-Plattform, die installiert ist. Auf diesem Windows 10-Gerät beispielsweise ist die Version 10.0.10240.0 der universellen Windows-Plattform installiert.

     ![Open the folder to view the versions installed](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

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

     ![Right click the project and choose Edit](../misc/media/uap-editproject.png "UAP_EditProject")

6. Find the \<PropertyGroup> element that contains the \<TargetPlatformVersion> element with a value of 8.1. Do the following steps for this \<PropertyGroup> element:

    1. Set the value of the \<Platform> element to: **x86**.

    2. Add a \<TargetPlatformIdentifier> element and set its value to: **UAP**.

    3. Change the existing value of the \<TargetPlatformVersion> element to be the value of the Universal Windows Platform version that you installed. Also add a \<TargetPlatformMinVersion> element and give it the same value.

    4. Change the value of the \<MinimumVisualStudioVersion> element to: **14**.

    5. Replace the \<ProjectTypeGuids> element as shown below:

         Für C#:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         Für VB:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. Add an \<EnableDotNetNativeCompatibleProfile> element and set its value to: **true**.

    7. Die standardmäßige Objektskalierung für universelle Windows-Apps liegt bei 200. If your project includes assets not scaled at 200, you will need to add a \<UapDefaultAssetScale> element with the value of the scale of your assets to this PropertyGroup. Erfahren Sie mehr mehr über [Objekte und Skalierungen](https://msdn.microsoft.com/library/jj679352.aspx).

         Now your \<PropertyGroup> element should look similar to this example:

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

8. Find \<PropertyGroup> elements that are configured for the AnyCPU platform as part of the Condition attribute. Entfernen Sie diese Elemente und alle ihre untergeordneten Elemente. AnyCPU wird für Windows 10-Apps in Visual Studio 2015 nicht unterstützt. For example, you should remove \<PropertyGroup> elements like these ones:

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

9. For each remaining \<PropertyGroup> element, check if the element has a Condition attribute with a Release configuration. If it does, but it does not contain a \<UseDotNetNativeToolchain> element, then add one. Set the value for the \<UseDotNetNativeToolchain> element to true, like this:

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

10. For Windows Phone projects only, remove the \<PropertyGroup> element that contains a \<TargetPlatformIdentifier> element with a value of WindowsPhoneApp. Entfernen Sie zudem alle untergeordneten Elemente dieses Elements:

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. Find the \<ItemGroup> element that contains the \<AppxManifest> element. Add the following \<None> element as a child of the \<ItemGroup> element:

    ```xml
    <None Include="project.json" />
    ```

12. Find the \<ItemGroup> element that contains other assets that are added to your project such as logo .png files (\<Content Include="Assets\Logo.scale-100.png" />). Add the following \<Content> child element to this \<ItemGroup> element:

     **For C#:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **For VB:**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. Find the \<ItemGroup> element that includes \<Reference> children elements to NuGet packages. Notieren Sie sich die NuGet-Pakete, die Sie verwenden, da Sie sie mit dem NuGet-Paket-Manager herunterladen müssen, nachdem Ihr Projekt erneut geladen wurde. Remove this \<ItemGroup> along with its children. Beispielsweise könnte ein UWP-Projekt die folgenden NuGet-Pakete aufweisen, die entfernt werden müssten:

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

## <a name="MigrateCPlusPlus"></a> Migrate your C++ Windows Store 8.1 or Windows Phone 8.1 apps to use the Universal Windows Platform

#### <a name="migrate-your-c-project-files"></a>Migrieren Ihrer C++-Projektdateien

1. Um zu erfahren, welche universelle Windows-Plattform installiert ist, öffnen Sie diesen Ordner: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Er enthält eine Liste der Ordner für jede universelle Windows-Plattform, die installiert ist. Der Ordnername ist die Version der universellen Windows-Plattform, die installiert ist. Auf diesem Windows 10-Gerät beispielsweise ist die Version 10.0.10240.0 der universellen Windows-Plattform installiert.

     ![Open the folder to view the versions installed](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Es kann mehr als eine Version der universellen Windows-Plattform installiert sein. Es wird empfohlen, dass Sie die neueste Version für Ihre App verwenden.

2. Öffnen Sie die Projektmappe, die Ihre vorhandene C++-Windows Store 8.1-App oder -Windows Phone 8.1-App in Visual Studio enthält.

     Klicken Sie mit der rechten Maustaste auf das vorhandene Projekts im Projektmappen-Explorer, und wählen Sie dann **Projekt entladen**. Nachdem das Projekt entladen wurde, klicken Sie mit der rechten Maustaste erneut auf die Projektdatei, und wählen Sie die Option zum Bearbeiten der VCXPROJ-Datei.

     ![Right&#45;click project file and choose to edit](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. Find the \<PropertyGroup> element that contains the \<ApplicationTypeRevision> element with a value of 8.1. Do the following steps for this \<PropertyGroup> element:

    1. Add a \<WindowsTargetPlatformVersion> element and a \<WindowsTargetPlatformMinVersion> element and give them the value of the Universal Windows Platform version that you installed.

    2. Aktualisieren Sie den Wert des Elements „ApplicationTypeRevision“ von „8.1“auf „10.0“.

    3. Change the value of the \<MinimumVisualStudioVersion> element to: 14.

    4. Add an \<EnableDotNetNativeCompatibleProfile> element and set its value to: true.

    5. Die standardmäßige Objektskalierung für universelle Windows-Apps liegt bei 200. If your project includes assets not scaled at 200, you will need to add a \<UapDefaultAssetScale> element with the value of the scale of your assets to this PropertyGroup. Erfahren Sie mehr mehr über [Objekte und Skalierungen](https://msdn.microsoft.com/library/jj679352.aspx).

    6. For Windows Phone projects only, change the value of \<ApplicationType> from Windows Phone to Windows Store.

         Now your \<PropertyGroup> element should look similar to this example:

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

4. Change all instances of the \<PlatformToolset> element to have the value v140. Beispiel:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. For each remaining \<PropertyGroup> element, check if the element has a Condition attribute with a Release configuration. If it does, but it does not contain a \<UseDotNetNativeToolchain> element, then add one. Set the value for the \<UseDotNetNativeToolchain> element to true, like this:

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

## <a name="PackageManifest"></a> Update your package manifest file for all your Windows Store 8.1 or Windows Phone 8.1 projects
 Sie müssen die Paketmanifestdatei für jedes Projekt in der Projektmappe aktualisieren.

#### <a name="update-your-package-manifest-file"></a>Aktualisieren der Paketmanifestdatei

1. Öffnen Sie die Datei „Package.appxmanifest“ im Projektmappen-Explorer. Sie müssen die Datei „Package.AppxManifest“ für jedes Windows Store- und Windows Phone-Projekt bearbeiten.

2. You need to update the \<Package> element with the new schemas based on your existing project type. Entfernen Sie zuerst die folgenden Schemas, je nachdem, ob Sie über ein Windows Store- oder ein Windows Phone-Projekt verfügen.

    **OLD for Windows Store project:** Your \<Package> element will look similar to this one.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **OLD for Windows Phone project:** Your \<Package> element will look similar to this one.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **NEW for Universal Windows Platform:** Add the schemas below to your \<Package> element. Entfernen Sie alle zugehörigen Namespace-Bezeichnerpräfixe von Elementen für die Schemas, die Sie gerade entfernt haben. Aktualisieren Sie die IgnorableNamespaces-Eigenschaft auf „uap mp“. Your new \<Package> element should look similar to this one.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. Add a \<Dependencies> child element to the \<Package> element. Then add a \<TargetDeviceFamily> child element to this \<Dependencies> element with Name, MinVersion, and MaxVersionTested attributes. Weisen Sie dem Name-Attribut den Wert „Windows.Universal“ zu. Geben Sie „MinVersion“ und „MaxVersionTested“ den Wert der installierten Version der universellen Windows-Plattform. Dieses Element sollte in etwa wie folgt aussehen:

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **For Windows Store only:** You need to add a \<mp:PhoneIdentity> child element to the \<Package> element. Fügen Sie ein „PhoneProductId“-Attribut und ein „PhonePublisherId“-Attribut hinzu. Set the PhoneProductId to have the same value as the Name attribute in the \<Identity> element. Legen Sie den „PhonePublishedId“-Wert auf Folgendes fest: 00000000-0000-0000-0000-000000000000. Und zwar so:

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. Find the \<Prerequisites> element and delete this element and any child elements that it has.

6. Add the **uap** namespace to the following \<Resource> elements: Scale, DXFeatureLevel. Beispiel:

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. Add the **uap** namespace to the following \<Capability> elements: documentsLibrary, picturesLibrary, videosLibrary, musicLibrary, enterpriseAuthentication, sharedUserCertificates, removableStorage, appointments, and contacts. Beispiel:

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. Add the **uap** namespace to the \<VisualElements> element and any of its child elements. Beispiel:

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

    **Gilt nur für Windows Store:** Die Namen der Kachelgröße wurden geändert. Change the attributes in the \<VisualElements> element to reflect the new converged tile sizes. 70 x 70 wird zu 71 x 71 und 30 x 30 zu 44 x 44.

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

9. Add the **uap** namespace to the \<ApplicationContentUriRules> and all its child elements. Beispiel:

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. Add the **uap** namespace to the following \<Extension> elements and all of its child elements: windows.accountPictureProvide,  windows.alarm, windows.appointmentsProvider windows.autoPlayContent,  windows.autoPlayDevice, windows.cachedFileUpdate, windows.cameraSettings, windows.fileOpenPicker, windows.fileTypeAssociation, windows.fileSavePicke, windows.lockScreenCall, windows.printTaskSettings, windows.protocol, windows.search, windows.shareTarget. Beispiel:

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

12. Ändern Sie die Framework-Abhängigkeiten. Add a Publisher name to all \<PackageDependency> elements, and specify a MinVersion if it’s not already specified.

     **OLD:** \<PackageDependency> element

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **NEW:** \<PackageDependency> element

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

     **OLD:**

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

     **OLD:**

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

    1. These attributes for \<VisualElements> are deprecated and should be removed:

       - The \<VisualElements> attributes: ForegroundText, ToastCapable

       - The \<DefaultTile> attribute DefaultSize

       - The \<ApplicationView> element

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

    1. Öffnen Sie den Datei-Explorer, klicken Sie in der Symbolleiste auf **Ansicht** , und wählen Sie **Ausgeblendete Elemente** und **Dateinamenerweiterungen**. Open this folder on your machine: \<path for the location of your solution>\\.vs\\{Project Name}\v14. Wenn eine Datei mit der Erweiterung .suo vorhanden ist, löschen Sie sie.

    2. Kehren Sie nun zurück zu dem Ordner, in dem sich die Projektmappe befindet. Öffnen Sie Ordner für Projekte, die in der Projektmappe vorhanden sind. Wenn eine Datei innerhalb eines dieser Projektordner über eine Erweiterung „.csproj.user“ oder „.vbproj.user“ verfügt, löschen Sie sie.

         Sie können Ihre Projektmappe nun wieder in Visual Studio öffnen. Sie können Ihre App nun mithilfe der universellen Windows-Plattform codieren, erstellen und debuggen.

         Erfahren Sie, wie Sie [Ihren Code anpassen können](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) , um die neuen Funktionen der universellen Windows-Plattform nutzen zu können.

## <a name="PreviousVersions"></a> Changes required for existing Universal Windows apps created with Visual Studio 2015 RC
 Wenn Sie universelle Windows 10-Apps mit Visual Studio 2015 RC erstellt haben, müssen Sie Ihr Projekt neu ausrichten, um die Version der UWP zu verwenden, die mit der neuesten Version von Visual Studio 2015 installiert wurde. Vorherige Versionen werden nicht unterstützt. Die erforderlichen Änderungen unterscheiden sich abhängig von der Sprache, die Sie zum Erstellen der App verwendet haben:

- [C#/VB apps](#RCUpdate10CSharp)

- [C++ apps](#RCUpdate10CPlusPlus)

### <a name="RCUpdate10CSharp"></a> Update your C#/VB projects to use the latest Universal Windows Platform
 Wenn Sie Ihre Projektmappe für Ihre vorhandene App öffnen, sehen Sie, dass für Ihre App eine Aktualisierung erforderlich ist:

 ![View your project in Solution Explorer](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 Wenn Sie das Projekt über den Projektmappen-Explorer erneut laden, wird dieses Dialogfeld angezeigt:

 ![Retarget your app to use the correct SDK](../misc/media/missingsdkforuap.png "MissingSDKforUAP")

 Da das universelle Windows-Plattform-SDK für Ihr Projekt nun nicht unterstützt wird, können Sie es nicht installieren. Klicken Sie auf „OK“, und befolgen Sie dann die folgenden Schritte.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Aktualisieren der C#/VB-Projekte zur Verwendung der neuesten universellen Windows-Plattform

1. Um zu erfahren, welche universelle Windows-Plattform installiert ist, öffnen Sie diesen Ordner: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Er enthält eine Liste der Ordner für jede universelle Windows-Plattform, die installiert ist. Der Ordnername ist die Version der universellen Windows-Plattform, die installiert ist. Auf diesem Windows 10-Gerät beispielsweise ist die Version 10.0.10240.0 der universellen Windows-Plattform installiert.

    ![Open the folder to view the versions installed](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

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

    ![Right click the project and choose Edit](../misc/media/uap-editproject.png "UAP_EditProject")

4. Find the \<PropertyGroup> element that contains the \<TargetPlatformVersion> and \<TargetPlatformMinVersion> elements. Change the existing value of the \<TargetPlatformVersion> and \<TargetPlatformMinVersion> elements to be the same version of the Universal Windows Platform that you have installed.

    Die standardmäßige Objektskalierung für universelle Windows-Apps liegt bei 200. Projects created with Visual Studio 2015 RC included assets scaled at 100, you will need to add a \<UapDefaultAssetScale> element with a value of 100 to this PropertyGroup. Erfahren Sie mehr mehr über [Objekte und Skalierungen](https://msdn.microsoft.com/library/jj679352.aspx).

5. Wenn Sie Verweise zu den SDKs für die UWP-Erweiterung (wie das Windows Mobile SDK) hinzugefügt haben, müssen Sie die SDK-Version aktualisieren. For example this \<SDKReference> element:

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

6. Find the \<Target> element with a name attribute that has the value: EnsureNuGetPackageBuildImports. Löschen Sie dieses Element und alle zugehörigen untergeordneten Elemente.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. Find and delete the \<Import> elements with Project and Condition attributes that reference Microsoft.Diagnostics.Tracing.EventSource and Microsoft.ApplicationInsights, like this:

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. Find the \<ItemGroup> that has \<Reference> children elements to NuGet packages. Notieren Sie sich die NuGet-Pakete, die referenziert wurden, da Sie diese Informationen in einem künftigen Schritt benötigen. Ein entscheidender Unterschied zwischen dem Windows 10-Projektformat zwischen Visual Studio 2015 RC und Visual Studio 2015 RTM besteht darin, dass das RTM-Format [NuGet](https://docs.microsoft.com/nuget/) Version 3 verwendet.

    Remove the \<ItemGroup> and all its children. Beispielsweise weist ein mit Visual Studio RC erstelltes UWP-Projekt die folgenden zu löschenden NuGet-Pakete auf:

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

9. Find the \<ItemGroup> element that contains an \<AppxManifest> element. If there is a \<None> element with an Include attribute set to: packages.config, delete it. Also, add a \<None> element with an Include attribute and set its value to: project.json.

10. Speichern Sie die Änderungen. Schließen Sie dann die Projektdatei.

11. Klicken Sie mit der rechten Maustaste auf die Projektdatei im Projektmappen-Explorer, und wählen Sie im Kontextmenü „Projekt erneut laden“. Alle Dateien im Projekt sollten nun im Projektmappen-Explorer angezeigt werden.

12. Wählen Sie die Datei „ApplicationInsights.config“ im Projektmappen-Explorer aus, und öffnen Sie die zugehörigen Eigenschaften. Legen Sie die Eigenschaft für die Buildaktion auf „Content“ fest, und kopieren Sie die Eigenschaft für das Ausgabeverzeichnis zu „Kopieren, wenn neuer“.

13. Öffnen Sie die Datei „Package.appxmanifest“ im Projektmappen-Explorer.

    1. Find the \<TargetDeviceFamily> element. Ändern Sie die zugehörigen Attribute „MinVersion“ und „MaxVersionTested“ auf die installierte Version der universellen Windows-Plattform. Und zwar so:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Speichern Sie die Änderungen.

14. Verwenden Sie den NuGet-Manager zum Hinzufügen der Pakete, die Sie im vorherigen Schritt gelöscht haben. Ein entscheidender Unterschied zwischen dem Windows 10-Projektformat zwischen Visual Studio 2015 RC und Visual Studio 2015 RTM besteht darin, dass das RTM-Format [NuGet](https://docs.microsoft.com/nuget/) Version 3 verwendet.

    Sie können Ihre App nun codieren, erstellen und debuggen.

    Wenn Sie über Komponententestprojekte für Ihre universellen Windows-Apps verfügen, müssen Sie zudem die [diese Schritte](#MigrateUnitTest)befolgen.

### <a name="RCUpdate10CPlusPlus"></a> Update your C++ projects to use the latest Universal Windows Platform

1. Um zu erfahren, welche universelle Windows-Plattform installiert ist, öffnen Sie diesen Ordner: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Er enthält eine Liste der Ordner für jede universelle Windows-Plattform, die installiert ist. Der Ordnername ist die Version der universellen Windows-Plattform, die installiert ist. Auf diesem Windows 10-Gerät beispielsweise ist die Version 10.0.10240.0 der universellen Windows-Plattform installiert.

     ![Open the folder to view the versions installed](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Es kann mehr als eine Version der universellen Windows-Plattform installiert sein. Es wird empfohlen, dass Sie die neueste Version für Ihre App verwenden.

2. Öffnen Sie die Projektmappe, die die universelle C++-Windows-App enthält. Klicken Sie mit der rechten Maustaste auf die VCXPROJ-Datei des Projekts, und wählen Sie die Option zum Entladen der Projektdatei. Nachdem das Projekt entladen wurde, klicken Sie mit der rechten Maustaste erneut auf die Projektdatei, und wählen Sie die Option zum Bearbeiten.

     ![Unload the project, then edit the project file](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. Find any \<PropertyGroup> elements that do not contain a Condition attribute but do contain an \<ApplicationTypeRevision> element. Aktualisieren Sie den Wert für „ApplicationTypeRevision“ von „8.2“ auf „10.0“. Add a \<WindowsTargetPlatformVersion> and a \<WindowsTargetPlatformMinVersion> element and set their values to be the value of the Universal Windows Platform version that you installed.

     Add an \<EnableDotNetNativeCompatibleProfile> element and set its value to true if the element does not already exist.

     Die standardmäßige Objektskalierung für universelle Windows-Apps liegt bei 200. Projects created with Visual Studio 2015 RC included assets scaled at 100, you will need to add a \<UapDefaultAssetScale> element with a value of 100 to this PropertyGroup. Erfahren Sie mehr mehr über [Objekte und Skalierungen](https://msdn.microsoft.com/library/jj679352.aspx).

     So this \<PropertyGroup> element will now be similar to this:

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

4. For each remaining \<PropertyGroup> element, check if the element has a Condition attribute with a Release configuration. If it does, but it does not contain a \<UseDotNetNativeToolchain> element, then add one. Set the value for the \<UseDotNetNativeToolchain> element to true, like this:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. You need to update the \<EnableDotNetNativeCompatibleProfile> element and the \<UseDotNetNativeToolchain> element to enable .NET Native, but .NET Native is not enabled in the C++ templates.

     Speichern Sie die Änderungen. Schließen Sie dann die Projektdatei.

6. Klicken Sie mit der rechten Maustaste auf die Projektdatei im Projektmappen-Explorer, und wählen Sie im Kontextmenü „Projekt erneut laden“. Alle Dateien im Projekt sollten nun im Projektmappen-Explorer angezeigt werden.

7. Öffnen Sie die Datei „Package.appxmanifest“ im Projektmappen-Explorer.

    1. Find the \<TargetDeviceFamily> element. Ändern Sie die zugehörigen Attribute „MinVersion“ und „MaxVersionTested“ auf die installierte Version der universellen Windows-Plattform. Und zwar so:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Speichern Sie die Änderungen.

         Sie können Ihre App nun codieren, erstellen und debuggen.

         Wenn Sie über Komponententestprojekte für Ihre universellen Windows-Apps verfügen, müssen Sie zudem die [diese Schritte](#MigrateUnitTest)befolgen.

## <a name="MigrateUnitTest"></a> Changes required for existing unit test projects for Universal Windows apps created with Visual Studio 2015 RC
 Wenn Sie Komponententestprojekte für universelle Windows 10-Apps mit Visual Studio 2015 RC erstellt haben, müssen Sie diese zusätzlichen Änderungen an Ihren Projektdateien vornehmen, um diese Testprojekte mit der neuesten Version von Visual Studio 2015 verwenden zu können. Die erforderlichen Änderungen unterscheiden sich abhängig von der Sprache, die Sie zum Erstellen der App verwendet haben:

- [C#/VB apps](#UnitTestRCUpdate10CSharp)

- [C++ apps](#UnitTestRCUpdate10CPlusPlus)

### <a name="UnitTestRCUpdate10CSharp"></a> Update your C#/VB unit test projects

1. Öffnen Sie unter Verwendung von Visual Studio Ihre Projektmappe, die Ihr C#-/VB-Komponententestprojekt enthält. Change the value of the \<OuttputType> element to: AppContainerExe.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Replace this element \<EnableCoreRuntime>false\</EnableCoreRuntime> with the following element:

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

4. Add this element \<UseDotNetNativeToolchain>true\</UseDotNetNativeToolchain> as a child element to these property groups:

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Delete the following \<ItemGroup> elements:

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

### <a name="UnitTestRCUpdate10CPlusPlus"></a> Update your C++ projects to use the latest Universal Windows Platform

1. Öffnen Sie unter Verwendung von Visual Studio Ihre Projektmappe, die Ihr C++-Komponententestprojekt enthält. Entfernen Sie das folgenden Elemente:

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Add the following \<ProjectConfiguration> elements below this element \<ItemGroup Label="ProjectConfigurations"> if they are not already in this fille:

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

4. Add these \<PropertyGroup> elements if they are not already in the file:

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

7. Add these \<ItemDefinitionGroup> elements in the section that already contains other \<ItemDefinitionGroup> elements:

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

8. Delete the following \< ItemGroup> element:

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Replace it with this \<ItemGroup> element:

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

9. Delete the following \< ItemGroup> element:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Replace it with these \<ItemGroup> elements:

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

     Replace it with these \<CICompile> elements:

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