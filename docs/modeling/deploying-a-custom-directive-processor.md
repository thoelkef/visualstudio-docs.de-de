---
title: Bereitstellen eines benutzerdefinierten Direktivenprozessors
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a10252d8465373c8637681763e59511b1e2d621
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596670"
---
# <a name="deploying-a-custom-directive-processor"></a>Bereitstellen eines benutzerdefinierten Direktivenprozessors

Wenn Sie einen benutzerdefinierten Direktivenprozessor in Visual Studio auf einem beliebigen Computer verwenden möchten, müssen Sie ihn mit einer der in diesem Thema beschriebenen Methoden registrieren.

Folgende Methoden stehen zur Auswahl:

- [Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md). Ermöglicht die Installation und Deinstallation des Anweisungsprozessors auf dem eigenen Computer und anderen Computern. Normalerweise können weitere Funktionen in der gleichen VSIX gebündelt werden.

- [VSPackage](../extensibility/internals/vspackages.md). Wenn Sie ein VSPackage definieren, das neben dem Anweisungsprozessor weitere Funktionen enthält, kann der Anweisungsprozessor einfach registriert werden.

- Festlegen eines Registrierungsschlüssels. Bei dieser Methode fügen Sie einen Registrierungseintrag für den Anweisungsprozessor hinzu.

Sie müssen eine dieser Methoden nur verwenden, wenn Sie Ihre Textvorlage in Visual Studio oder MSBuild transformieren möchten. Falls Sie in der Anwendung einen benutzerdefinierten Host verwenden, ist dieser für die Suche nach Direktivenprozessoren für die einzelnen Direktiven zuständig.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>Bereitstellen eines Direktivenprozessors in einer VSIX

Sie können einer [Visual Studio-Erweiterung (VSIX)](../extensibility/starting-to-develop-visual-studio-extensions.md)einen benutzerdefinierten Direktivenprozessor hinzufügen.

 Stellen Sie sicher, dass die VSIX-Datei die folgenden zwei Elemente enthält:

- Die Assembly (.dll), die die benutzerdefinierte Direktivenprozessorklasse enthält.

- Eine PKGDEF-Datei, durch die der Anweisungsprozessor registriert wird. Der Stammname der Datei muss mit dem Namen der Assembly identisch sein. Die Dateinamen können z. B. "CDP.dll" und "CDP.pkgdef" lauten.

Wenn Sie den Inhalt einer VSIX-Datei überprüfen oder ändern möchten, ändern Sie die Dateinamenerweiterung in .zip, und öffnen Sie die Datei dann. Ändern Sie den Dateinamen wieder in .vsix, nachdem Sie den Inhalt bearbeitet haben.

Zum Erstellen einer VSIX-Datei stehen mehrere Methoden zur Verfügung. Im folgenden Verfahren wird eine Methode beschrieben.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>So entwickeln Sie einen benutzerdefinierten Anweisungsprozessor in einem VSIX-Projekt

1. Erstellen Sie ein neues **VSIX-Projekt** Projekt.

2. Legen Sie in **Source. Extension. vsixmanifest**den Inhaltstyp und die unterstützten Editionen fest.

    1. Wählen Sie im VSIX-Manifest-Editor auf der Registerkarte **Objekte** die Option **neu** aus, und legen Sie die Eigenschaften des neuen Elements fest:

         **Inhaltstyp** = **VSPackage**

         **Quell Projekt** = \<*das aktuelle Projekt*>

    2. Klicken Sie auf **ausgewählte Editionen** , und überprüfen Sie die Installationstypen, für die der Direktivenprozessor verwendet werden soll.

3. Fügen Sie eine PKGDEF-Datei hinzu, und legen Sie die Eigenschaften fest, die in die VSIX eingeschlossen werden sollen.

    1. Erstellen Sie eine Textdatei, und nennen Sie Sie \<*AssemblyName*>. pkgdef.

         \<*AssemblyName*> ist in der Regel mit dem Namen des Projekts identisch.

    2. Wählen Sie die Datei im Projektmappen-Explorer aus, und legen Sie die Eigenschaften wie folgt fest:

         **Buildvorgang** = **Inhalt**

         **In Ausgabeverzeichnis kopieren** = **immer kopieren**

         **In VSIX einschließen** = **true**

    3. Legen Sie den Namen der VSIX fest, und stellen Sie sicher, dass die ID eindeutig ist.

4. Fügen Sie der PKGDEF-Datei den folgenden Text hinzu:

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     Ersetzen Sie die folgenden Namen durch eigene Namen: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.

5. Fügen Sie dem Projekt die folgenden Verweise hinzu:

    - **Microsoft.VisualStudio.TextTemplating.\*.0**

    - **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**

    - **Microsoft.VisualStudio.TextTemplating.VSHost.\*.0**

6. Fügen Sie dem Projekt die benutzerdefinierte Direktivenprozessorklasse hinzu.

     Dies ist eine öffentliche Klasse, die <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> oder <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementieren muss.

#### <a name="to-install-the-custom-directive-processor"></a>So installieren Sie den benutzerdefinierten Anweisungsprozessor

1. Öffnen Sie in Windows-Explorer das Buildverzeichnis (normalerweise "bin\debug" oder "Bin\Release").

2. Wenn Sie den Anweisungsprozessor auf einem anderen Computer installieren möchten, kopieren Sie die VSIX-Datei auf den anderen Computer.

3. Doppelklicken Sie auf die VSIX-Datei. Der Installer für die Visual Studio-Erweiterung wird angezeigt.

4. Starten Sie Visual Studio neu. Sie können jetzt Textvorlagen mit Anweisungen ausführen, die auf den benutzerdefinierten Anweisungsprozessor verweisen. Jede Direktive besitzt das folgende Format:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>So deinstallieren Sie den benutzerdefinierten Anweisungsprozessor oder deaktivieren Sie ihn vorübergehend

1. Klicken Sie im Visual **Studio-** Menü Extras auf **Erweiterungs-Manager**.

2. Wählen Sie die VSIX mit dem Direktivenprozessor aus, und klicken Sie dann auf **deinstallieren** oder **Deaktivieren**.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Problembehandlung für einen Direktivenprozessor in einer VSIX
 Die folgenden Hinweise können bei Problemen mit dem Anweisungsprozessor hilfreich sein:

- Der in der benutzerdefinierten Anweisung angegebene Prozessorname muss dem `CustomDirectiveProcessorName` entsprechen, den Sie in der PKGDEF-Datei angegeben haben.

- Die `IsDirectiveSupported`-Methode muss `true` zurückgeben, wenn der Name der `CustomDirective` an sie übergeben wird.

- Wenn die Erweiterung im Erweiterungs-Manager nicht angezeigt wird, aber das System die Installation nicht zulässt, löschen Sie die Erweiterung aus **%LocalAppData%\microsoft\visualstudio\\\*0 \ Extensions\\** .

- Öffnen Sie die VSIX-Datei, und überprüfen Sie den Inhalt. Ändern Sie die Dateierweiterung in .zip, um die Datei zu öffnen. Vergewissern Sie sich, dass sie die DLL-, PKGDEF- und extension.vsixmanifest-Dateien enthält. Die extension.vsixmanifest-Datei sollte die entsprechende Liste im Knoten "SupportedProducts" und einen Knoten "VsPackage" unter dem Knoten "Inhalt" enthalten:

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Bereitstellen eines Anweisungsprozessors in einem VSPackage
 Wenn der Direktivenprozessor Teil eines VSPackage ist, das im GAC installiert wird, können Sie die PKGDEF-Datei vom System generieren lassen.

 Fügen Sie das folgende Attribut in der Paketklasse ein:

```csharp
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
> Dieses Attribut wird in der Paketklasse eingefügt, nicht der Anweisungsprozessorklasse.

 Die PKGDEF-Datei wird generiert, wenn Sie das Projekt erstellen. Beim Installieren des VSPackage wird der Direktivenprozessor von der PKGDEF-Datei registriert.

 Überprüfen Sie, ob die PKGDEF-Datei im Buildordner angezeigt wird (normalerweise „bin\Debug“ oder „bin\Release“). Falls sie nicht angezeigt wird, öffnen Sie die CSPROJ-Datei in einem Text-Editor, und entfernen Sie den folgenden Knoten: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`

 Weitere Informationen finden Sie unter [VSPackages](../extensibility/internals/vspackages.md).

## <a name="setting-a-registry-key"></a>Festlegen eines Registrierungsschlüssels
 Diese Methode zum Installieren eines benutzerdefinierten Anweisungsprozessors wird am seltensten verwendet. Bei dieser Methode ist das Aktivieren und Deaktivieren des Direktivenprozessors komplizierter, und der Direktivenprozessor kann nicht an andere Benutzer verteilt werden.

> [!CAUTION]
> Durch eine fehlerhafte Bearbeitung der Registrierung kann das System ernsthaft beschädigt werden. Bevor Sie Änderungen an der Registrierung vornehmen, sollten Sie daher unbedingt alle wichtigen Daten auf dem Computer sichern.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>So registrieren Sie einen Anweisungsprozessor durch Festlegen eines Registrierungsschlüssels

1. Führen Sie aus `regedit`.

2. Navigieren Sie in regedit zum folgenden Eintrag:

    **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\\\*. 0 \ texttemplating\directiveprozessoren**

    Wenn Sie den Direktivenprozessor in der experimentellen Version von Visual Studio installieren möchten, fügen Sie "EXP" nach "11,0" ein.

3. Fügen Sie einen Registrierungsschlüssel mit dem Namen der Anweisungsprozessorklasse hinzu.

   - Klicken Sie in der Registrierungs Struktur mit der rechten Maustaste auf den Knoten **directiveprozessoren** , zeigen Sie auf **neu**, und klicken Sie dann auf **Schlüssel**.

4. Fügen Sie im neuen Knoten entsprechend den folgenden Tabellen Zeichenfolgenwerte für "Class" und "CodeBase" oder "Assembly" hinzu.

   1. Klicken Sie mit der rechten Maustaste auf den von Ihnen erstellten Knoten, zeigen Sie auf **neu**, und klicken Sie dann auf **Zeichen folgen Wert**.

   2. Bearbeiten Sie den Namen des Werts.

   3. Doppelklicken Sie auf den Namen, und bearbeiten Sie die Daten.

   Wenn der benutzerdefinierte Direktivenprozessor nicht im GAC ist, sollten die Registrierungsunterschlüssel den Angaben in der folgenden Tabelle entsprechen:

|-Name|Typ|importieren|
|-|-|-|
|(Standardeinstellung)|REG_SZ|(Wert nicht festgelegt)|
|Klasse|REG_SZ|**\<Namespace Name >.\<Klassen Name >**|
|CodeBase|REG_SZ|**\<Sie Ihren Pfad >\\< Ihren Assemblynamen\>**|

 Wenn die Assembly im GAC ist, sollten die Registrierungsunterschlüssel den Angaben in der folgenden Tabelle entsprechen:

|-Name|Typ|importieren|
|-|-|-|
|(Standardeinstellung)|REG_SZ|(Wert nicht festgelegt)|
|Klasse|REG_SZ|\<**Sie den voll qualifizierten Klassennamen**>|
|Assembly|REG_SZ|\<**Sie den Assemblynamen im GAC**>|

## <a name="see-also"></a>Siehe auch

- [Erstellen von benutzerdefinierten T4-Anweisungsprozessoren für Textvorlagen](../modeling/creating-custom-t4-text-template-directive-processors.md)
