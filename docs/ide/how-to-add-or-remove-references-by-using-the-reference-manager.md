---
title: "Vorgehensweise: Hinzufügen und Entfernen von Verweisen mit dem Verweis-Manager | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: aefd0227717352e449b51950620d0f0900cf2e60
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Vorgehensweise: Hinzufügen und Entfernen von Verweisen mit dem Verweis-Manager

Sie können das Dialogfeld **Verweis-Manager** verwenden, um Verweise auf Komponenten hinzuzufügen und zu verwalten, die von Ihnen, Microsoft oder einem anderen Unternehmen entwickelt wurden. Wenn Sie eine universelle Windows-App entwickeln, verweist das Projekt automatisch auf alle richtigen Windows SDK-DLLs. Wenn Sie eine Anwendung für .NET entwickeln, verweist das Projekt automatisch auf mscorlib.dll. Einige .NET-APIs werden in Komponenten verfügbar gemacht, die Sie manuell hinzufügen müssen. Verweise auf COM-Komponenten oder benutzerdefinierte Komponenten müssen manuell hinzugefügt werden.

## <a name="reference-manager-dialog-box"></a>Dialogfeld "Verweis-Manager"

Das Dialogfeld **Verweis-Manager** zeigt die verschiedenen Kategorien je nach Projekttyp auf der linken Seite an:

- [Assemblys:](#assemblies) mit den Untergruppen „Framework“ und „Erweiterungen“.

- [COM:](#com) Hier werden alle COM-Komponenten aufgelistet, die für Verweise verfügbar sind.

- [Projektmappe:](#solution) mit der Projektuntergruppe

- [Fenster:](#windows) mit den Untergruppen „Kernspeicher“ und „Erweiterungen“. Sie können die Verweise im Windows SDK oder im Erweiterungs-SDK mit dem **Objektkatalog** untersuchen.

- [Durchsuchen:](#browse) mit der Untergruppe „Aktuell“

## <a name="adding-and-removing-a-reference"></a>Hinzufügen und Entfernen von Verweisen

### <a name="to-add-a-reference"></a>So fügen Sie einen Verweis hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten „Verweise“, und klicken Sie dann auf **Verweis hinzufügen**.

2. Geben Sie die hinzuzufügenden Verweise an, und wählen Sie dann die Schaltfläche **OK** aus.

   Der **Verweis-Manager** wird mit den verfügbaren Verweisen nach Gruppe geöffnet.

## <a name="a-idassemblies-assemblies-tab"></a><a id="assemblies" />Registerkarte „Assemblys“

Die Registerkarte **Assemblys** führt alle .NET Framework-Assemblys auf, die für Verweise verfügbar sind. Die Registerkarte **Assemblys** führt keine Assemblys aus dem globalen Assemblycache (GAC) auf, da Assemblys im GAC Teil der Laufzeitumgebung sind. Wenn Sie eine Anwendung bereitstellen oder kopieren, die einen Verweis auf eine im GAC registrierte Assembly enthält, wird die Komponente unabhängig von der Einstellung „Lokal kopieren“ nicht mit der Anwendung bereitgestellt oder kopiert. Weitere Informationen finden Sie unter [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md).

Wenn Sie manuell einen Verweis auf einen der EnvDTE-Namespaces (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a oder EnvDTE100) hinzufügen, legen Sie im Eigenschaftenfenster die Eigenschaft **Interoptypen einbetten** des Verweises auf **FALSE** fest. Wird diese Eigenschaft auf **TRUE** festgelegt wird, können aufgrund bestimmter EnvDTE-Eigenschaften, die nicht eingebettet werden können, Buildprobleme auftreten.

Alle Desktopprojekte enthalten einen impliziten Verweis auf "mscorlib". [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Projekte enthalten einen impliziten Verweis auf Microsoft.VisualBasic. Alle Projekte enthalten einen impliziten Verweis auf System.Core. Dies gilt auch, wenn der Eintrag aus der Liste der Verweise entfernt wird.

Wenn ein Projekttyp keine Assemblys unterstützt, wird die Registerkarte nicht im Dialogfeld **Verweis-Manager** angezeigt.

Die Assemblyregisterkarte besteht aus zwei Unterregisterkarten:

1. In **Framework** werden alle Assemblys aufgelistet, die das Zielframework darstellen.

    Projekte für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps enthalten bei Projekterstellung standardmäßig Verweise auf alle Assemblys im verwendeten [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)]. In verwalteten Projekten gibt ein schreibgeschützter Knoten unter dem Ordner „Verweise“ im **Projektmappen-Explorer** den Verweis für das gesamte Framework an. Entsprechend listet die Frameworkregisterkarte keine der Assemblys aus dem Framework auf und zeigt stattdessen die folgende Meldung an: „Alle der Framework-Assemblys sind bereits referenziert. Verwenden Sie den Objektkatalog, um Verweise im Framework zu durchsuchen“. Für Desktopprojekte werden auf der Registerkarte „Framework“ Assemblys aus dem Zielframework aufgezählt, und der Benutzer muss die für die Anwendung erforderlichen Verweise hinzufügen.

2. Unter **Erweiterungen** werden alle Assemblys aufgelistet, die externe Anbieter von Komponenten und Steuerelementen selbst entwickelt haben, um das Zielframework zu erweitern. Abhängig vom Zweck der Benutzeranwendung sind diese Assemblys gegebenenfalls erforderlich.

    - Erweiterungen werden ausgefüllt, indem die Assemblys aufgelistet werden, die in den folgenden Speicherorten registriert sind:

        ```
        32-bit machine:
        HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        64-bit machine:
        HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        And older versions of the [Target Framework Identifier]  
        ```

        Wenn ein Projekt .NET Framework 4 als Ziel auf einem 32-Bit-Computer verwendet, listen die Erweiterungen Assemblys auf, die unter \Microsoft\\.NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\ .NETFramework\v3.5 \AssemblyFoldersEx\\, \Microsoft\\.NETFramework\v3.0\AssemblyFoldersEx\\ und \Microsoft\\.NETFramework\v2.0\AssemblyFoldersEx\\ registriert sind.

Einige Komponenten in der Liste werden möglicherweise nicht angezeigt. Dies hängt von der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Version des Projekts ab. Dieser Fall kann unter den folgenden Bedingungen eintreten:

- Eine Komponente, für die eine aktuelle Version von .NET Framework verwendet wird, ist nicht kompatibel mit einem Projekt, für das eine frühere Version von .NET Framework als Zielversion festgelegt wurde.

    Informationen zum Ändern der Zielversion von .NET Framework für ein Projekt finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Eine Komponente, für die [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] verwendet wird, ist nicht kompatibel mit einem Projekt, für das als Zielversion [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] festgelegt wurde.

    Wenn Sie eine neue Anwendung erstellen, wird für einige Projekte standardmäßig als Zielversion [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] festgelegt.

- Sie sollten keine Dateiverweise auf Ausgaben eines anderen Projekts in derselben Projektmappe hinzufügen, da dies zu Kompilierungsfehlern führen kann. Erstellen Sie Verweise zwischen Projekten stattdessen im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **Projekte**. Dies erleichtert die Entwicklung im Team, da die in den Projekten erstellten Klassenbibliotheken besser verwaltet werden können. Weitere Informationen finden Sie unter [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> In Visual Studio 2015 oder höher wird anstelle eines Projektverweises ein Dateiverweis erstellt, wenn die Zielversion von .NET Framework eines Projekts Version 4.5 oder höher ist und die Zielversion des anderen Projekts Version 2, 3, 3.5 oder 4.0 ist.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>So zeigen Sie eine Assembly im Dialogfeld "Verweis hinzufügen" an

- Verschieben oder kopieren Sie die Assembly in einen der folgenden Speicherorte:

    - Das aktuelle Projektverzeichnis. (Sie können die Assemblys über die Registerkarte **Durchsuchen** suchen.)

    - Andere Projektverzeichnisse in der gleichen Projektmappe. (Sie können die Assemblys über die Registerkarte **Projekte** suchen.)

    \- oder –

- Legen Sie einen Registrierungsschlüssel fest, der den Speicherort der anzuzeigenden Assemblys angibt:

    Fügen Sie für ein 32-Bit-Betriebssystem einen der folgenden Registrierungsschlüssel hinzu:

    - [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

    - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

    Fügen Sie für ein 64-Bit-Betriebssystem einen der folgenden Registrierungsschlüssel in einer 32-Bit-Registrierungsstruktur hinzu:

    - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

    - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

    *VersionMinimum* ist die niedrigste geltende .NET Framework-Version. Wenn *VersionMinimum* v3.0 ist, gelten in „AssemblyFoldersEx“ angegebene Ordner für Projekte mit der Zielversion .NET Framework 3.0 und höher.

    *AssemblyLocation* ist das Verzeichnis der Assemblys, die Sie im Dialogfeld **Verweis hinzufügen** anzeigen möchten, z.B. C:\MyAssemblies\\.

    Indem der Registrierungsschlüssel unter dem HKEY_LOCAL_MACHINE-Knoten erstellt wird, können die Assemblys am angegebenen Speicherort von allen Benutzern im Dialogfeld **Verweis hinzufügen** angezeigt werden. Wenn der Registrierungsschlüssel unter dem HKEY_CURRENT_USER-Knoten erstellt wird, hat dies nur Einfluss auf die Einstellung für den aktuellen Benutzer.

    Öffnen Sie das Dialogfeld **Verweis hinzufügen** erneut. Die Assemblys sollten auf der Registerkarte **.NET** angezeigt werden. Stellen Sie andernfalls sicher, dass sich die Assemblys im angegebenen Verzeichnis *AssemblyLocation* befinden, starten Sie Visual Studio neu, und versuchen Sie es noch einmal.

## <a name="a-idcom-com-tab"></a><a id="com" />Registerkarte „COM“

Die Registerkarte "COM" listet alle COM-Komponenten auf, die für Verweise verfügbar sind. Wenn Sie einer registrierten COM DLL mit einem internen Manifest eine Referenz hinzufügen möchten, müssen Sie die Registrierung der DLL zunächst aufheben. Andernfalls fügt Visual Studio den Assemblyverweis als ActiveX-Steuerelement und nicht als systemeigene DLL hinzu.

Wenn ein Projekttyp COM nicht unterstützt, wird die Registerkarte nicht im Dialogfeld **Verweis-Manager** angezeigt.

## <a name="a-idsolution-solution-tab"></a><a id="solution" />Registerkarte „Projektmappe“

Die Registerkarte "Projektmappe" listet alle kompatiblen Projekte innerhalb der aktuellen Projektmappe, auf der Unterregisterkarte "Projekte" auf.

Ein Projekt kann auf ein anderes Projekt verweisen, das eine andere .NET Framework-Version als Ziel verwendet. Beispielsweise können Sie ein Projekt erstellen, das [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] als Ziel verwendet, jedoch auf eine Assembly verweist, die für .NET Framework 2. erstellt wurde. Das .NET Framework 2-Projekt kann jedoch nicht auf ein [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]-Projekt verweisen. Weitere Informationen finden Sie unter [Festlegen einer bestimmten .NET-Framework-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md).

Ein Projekt, das [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] als Ziel verwendet, ist nicht kompatibel mit einem Projekt, für das als Zielversion [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] festgelegt wurde.

Falls ein Projekt auf .NET Framework 4 und ein anderes auf eine frühere Version ausgerichtet ist, wird anstelle eines Projektverweises ein Dateiverweis erstellt.

Ein Projekt für [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] kann einem Projekt, das auf .NET Framework ausgerichtet ist, keinen Projektverweis hinzufügen und umgekehrt.

## <a name="a-idwindows-windows-tab"></a><a id="windows" />Registerkarte „Fenster“

Die Registerkarte "Fenster" führt alle SDK auf, die für Plattformen gelten, auf denen Windows-Betriebssysteme ausgeführt werden.

Sie können eine WinMD-Datei in Visual Studio auf zwei Arten generieren:

- Von der **[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-App verwaltete Projekte**: [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-App-Projekte können WinMD-Binärdateien ausgeben, indem Projekteigenschaften &#124; Ausgabetyp = WinMD-Datei festgelegt wird. Der WinMD-Dateiname muss der Superset-Namespace aller Namespaces sein, die innerhalb des Namespace vorhanden sind. Wenn ein Projekt beispielsweise aus Namespaces A.B und A.B.C besteht, sind die möglichen Namen für das ausgegebene WinMD A.winmd und A.B.winmd. Wenn ein Benutzer einen Wert „Projekteigenschaften &#124; Assemblyname“ oder „Projekteigenschaften &#124; Namespace“ eingibt, der nicht mit dem Satz von Namespaces im Projekt zusammenhängt, wenn kein Superset-Namespace innerhalb eines Projekts vorhanden ist, wird eine Buildwarnung generiert: 'A.winmd' isn't a valid .winmd file name for this assembly ('A.winmd' ist kein gültiger WINMD-Dateiname für diese Assembly). Alle Typen innerhalb einer Windows-Metadatendatei müssen in einem Subnamespace des Dateinamens vorhanden sein. Typen, die nicht in einem Subnamespace des Dateinamens vorhanden sind, können zur Laufzeit nicht lokalisiert werden. In dieser Assembly ist der kleinste allgemeine Namespace "CSWSClassLibrary1". Ein Visual Basic- oder C#-Desktopprojekt kann nur WinMDs nutzen, die mit [!INCLUDE[win8](../debugger/includes/win8_md.md)]-SDKs generiert werden. Diese werden als Erstanbieter-WinMDs bezeichnet und können keine WinMDs generieren.

- Native **[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-App-Projekte**: Eine native WinMD-Datei besteht nur aus Metadaten. Die Implementierung befindet sich in einer separaten DLL-Datei. Native Binärdateien lassen sich erzeugen, indem Sie die Projektvorlage der Komponente für Windows Runtime im Dialogfeld **Neues Projekt** auswählen wird oder durch Starten in einem leeren Projekt und Ändern der Projekteigenschaften, um eine WinMD-Datei zu generieren. Wenn das Projekt aus unzusammenhängenden Namespaces besteht, wird ein Buildfehler mit der Empfehlung angezeigt, eigene Namespaces zu kombinieren oder das MSMerge-Tool auszuführen.

Die Registerkarte "Windows" besteht aus zwei Untergruppen.

### <a name="core-subgroup"></a>Untergruppe „Kernspeicher“

Die Untergruppe "Core" listet alle WinMDs (für Windows Runtime-Elemente) im SDK für die jeweilige Windows-Version auf.

[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-App-Projekte enthalten bei Projekterstellung standardmäßig Verweise auf alle WinMDs im [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK. In verwalteten Projekten gibt ein schreibgeschützter Knoten unter dem Ordner „Verweise“ im **Projektmappen-Explorer** den Verweis für das gesamte [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK an. Entsprechend listet die Untergruppe „Core“ im Verweis-Manager keine der Assemblys aus dem [!INCLUDE[win8](../debugger/includes/win8_md.md)]-SDK auf, sondern zeigt stattdessen eine Meldung an: „The Windows SDK is already referenced. Please use the Object Browser to explore the references in the Windows SDK.“ („Windows SDK ist bereits referenziert. Verwenden Sie den Objektkatalog, um die Verweise im Windows SDK zu durchsuchen.“)

In den Desktopprojekten wird die Core-Untergruppe nicht standardmäßig angezeigt. Sie können die Windows-Runtime hinzufügen, indem Sie das Kontextmenü für den Projektknoten öffnen, **Projekt entladen** auswählen, den folgenden Codeabschnitt hinzufügen, und das Projekt erneut öffnen (indem Sie auf dem Projektknoten **Projekt erneut laden** wählen). Wenn Sie das Dialogfeld **Verweis-Manager** aufrufen, wird die Untergruppe „Core“ angezeigt.

```xml
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

Vergessen Sie nicht, das Kontrollkästchen **Windows** in dieser Untergruppe zu aktivieren. Anschließend können Windows-Runtime-Elemente verwendet werden. Allerdings sollten Sie auch System.Runtime hinzufügen. Die Windows-Runtime definiert einige Standardklassen und Schnittstellen (beispielsweise IEnumerable ), die in Windows Runtime-Bibliotheken verwendet werden. Informationen über das Hinzufügen von System.Runtime finden Sie unter [Verwaltete Desktop-Apps und Windows-Runtime](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).

### <a name="extensions-subgroup"></a>Untergruppe „Erweiterungen“

Erweiterungen listen die Benutzer-SDKs auf, die die als Ziel verwendete Windows-Plattform erweitern. Diese Registerkarte wird nur für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-App-Projekte angezeigt. Desktopprojekte zeigen diese Registerkarte nicht an, da sie nur WINMD-Dateien von Erstanbietern nutzen können.

Ein SDK ist eine Auflistung von Dateien, die Visual Studio als einzelne Komponente behandelt. Auf der Erweiterungsregisterkarte werden SDKs, die sich auf das Projekt beziehen, über das das Dialogfeld **Verweis-Manager** aufgerufen wurde, als einzelne Einträge aufgeführt. Wenn er einem Projekt hinzugefügt wird, wird der gesamte SDK-Inhalt von Visual Studio so verwendet, dass der Benutzer keine weiteren Aktionen ausführen muss, um den SDK-Inhalt in IntelliSense, in der Toolbox, in Designern, im Objektkatalog, im Build, bei der Bereitstellung, beim Debuggen und beim Packen zu nutzen. Informationen über das Anzeigen Ihres SDKs auf der Registerkarte „Erweiterungen“ finden Sie unter [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Wenn ein Projekt auf ein SDK verweist, das von einem anderen SKD abhängt, verwendet Visual Studio das zweite SDK nur, wenn der Benutzer einen Verweis auf das zweite SDK manuell hinzufügt. Wenn ein Benutzer ein SDK auf der Registerkarte **Erweiterungen** auswählt, kann der Benutzer mithilfe des Dialogfelds **Verweis-Manager** SDK-Abhängigkeiten identifizieren, indem nicht nur der Name und die Version des SDKs, sondern auch der Name aller SDK-Abhängigkeiten im Detailbereich aufgelistet werden. Wenn ein Benutzer die Abhängigkeiten nicht identifiziert und nur dieses SDK hinzufügt, fordert MSBuild den Benutzer auf, die Abhängigkeiten hinzuzufügen.

Wenn ein Projekttyp keine **Erweiterungen** unterstützt, wird die Registerkarte nicht im Dialogfeld **Verweis-Manager** angezeigt.

## <a name="a-idbrowse-browse-button"></a><a id="browse" />Schaltfläche „Durchsuchen“

Mit der Schaltfläche **Durchsuchen** können Sie nach einer Komponente im Dateisystem suchen.

Ein Projekt kann auf eine Komponente verweisen, die eine andere .NET Framework-Version als Ziel verwendet. Beispielsweise können Sie eine Anwendung mit .NET Framework 4.7 als Ziel erstellen, das auf eine Komponente mit .NET Framework 4 als Zielversion verweist. Weitere Informationen finden Sie unter [Festlegen einer bestimmten .NET-Framework-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md).

Sie sollten keine Dateiverweise auf Ausgaben eines anderen Projekts in derselben Projektmappe hinzufügen, da dies zu Kompilierungsfehlern führen kann. Erstellen Sie Verweise zwischen Projekten stattdessen im Dialogfeld **Verweis-Manager** auf der Registerkarte **Projektmappe**. Dies erleichtert die Entwicklung im Team, da die in den Projekten erstellten Klassenbibliotheken besser verwaltet werden können. Weitere Informationen finden Sie unter [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md).

Sie können nicht zu einem SDK navigieren und es dem Projekt hinzufügen. Sie können nur zu einer Datei navigieren (beispielsweise eine Assembly oder einer WINMD-Datei) und es dem Projekt hinzufügen.

Beim Erstellen eines Dateiverweises auf ein WinMD wird als Layout erwartet, dass die *FileName*winmd-, *FileName*.dll- und *FileName*.pri-Dateien alle nebeneinander platziert werden. Wenn Sie in den folgenden Szenarien auf ein WinMD verweisen, wird ein unvollständiger Satz von Dateien in das Projektausgabeverzeichnis kopiert und es treten infolgedessen Build- und Laufzeitfehler auf.

- **Native Komponente**: Ein natives Projekt erstellt ein WinMD für jeden unzusammenhängenden Satz von Namespaces und eine DLL, die aus der Implementierung besteht. Die WinMDs haben unterschiedliche Namen. Wenn auf diese native Komponentendatei verwiesen wird, erkennt MSBuild nicht, dass die ungleich benannten WinMDs eine Komponente darstellen. Folglich werden nur die *FileName*.dll- und *FileName*.winmd-Dateien mit identischem Namen kopiert, und es treten Laufzeitfehler auf. Um dieses Problem zu umgehen, erstellen Sie eine Erweiterungs-SDK. Weitere Informationen finden Sie unter [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md).

- **Verarbeiten von Steuerelementen**: Mindestens ein XAML-Steuerelement besteht aus einer *FileName*.winmd, *FileName*.dll, *FileName*.pri, *XamlName*.xaml und einer *ImageName*.jpg. Bei der Projekterstellung werden die Ressourcendateien, die mit dem Dateiverweis verknüpft sind, nicht in das Ausgabeverzeichnis des Projekts kopiert. Es werden nur die Dateien *FileName*.winmd, *FileName*.dll und *FileName*.pri kopiert. Ein Buildfehler wird protokolliert, um den Benutzer zu informieren, dass die Ressourcen *XamlName*.xaml und *ImageName*.jpg fehlen. Damit der Vorgang erfolgreich abgeschlossen wird, muss der Benutzer diese Ressourcendateien manuell in das Projektausgabeverzeichnis für Build und Debuggen/Laufzeit kopieren. Um dieses Problem zu umgehen, erstellen Sie entweder eine Erweiterungs-SDK, indem Sie die Schritte unter [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md) ausführen, oder bearbeiten Sie die Projektdatei, und fügen Sie folgende Eigenschaft hinzu:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Wenn Sie die Eigenschaft hinzufügen, wird der Build ggf. langsamer ausgeführt.

## <a name="recent"></a>Zuletzt

Assemblys, COM, Windows und Durchsuchen unterstützen jeweils eine Registerkarte "Aktuell", auf der die Liste der Komponenten aufgeführt werden, die Projekten kürzlich hinzugefügt wurden.

## <a name="search"></a>Suche

Die Suchleiste im Dialogfeld **Verweis-Manager** funktioniert über die Registerkarte, die sich im Fokus befindet. Wenn beispielsweise ein Benutzer „System“ in der Suchleiste eingibt, während die Registerkarte **Projektmappe** im Fokus ist, gibt die Suche keine Ergebnisse zurück, es sei denn, die Projektmappe umfasst einen Projektnamen, der das Wort „System“ enthält.

## <a name="see-also"></a>Siehe auch

[Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)
