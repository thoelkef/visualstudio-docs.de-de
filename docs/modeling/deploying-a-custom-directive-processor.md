---
title: "Deploying a Custom Directive Processor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, custom directive processors"
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 18
---
# Deploying a Custom Directive Processor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie auf einem Computer einen benutzerdefinierten Direktivenprozessor in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwenden möchten, müssen Sie ihn anhand einer der in diesem Thema beschriebenen Methoden registrieren.  
  
 Folgende Methoden stehen zur Auswahl:  
  
-   [Visual Studio\-Erweiterung \(VSIX\)](http://msdn.microsoft.com/de-de/64ff1452-f7d5-42d9-98b8-76f769f76832).  Ermöglicht die Installation und Deinstallation des Direktivenprozessors auf dem eigenen Computer und anderen Computern.  Normalerweise können weitere Funktionen in der gleichen VSIX gebündelt werden.  
  
-   [VSPackage](../extensibility/internals/vspackages.md).  Wenn Sie ein VSPackage definieren, das neben dem Direktivenprozessor weitere Funktionen enthält, kann der Direktivenprozessor einfach registriert werden.  
  
-   Festlegen eines Registrierungsschlüssels.  Bei dieser Methode fügen Sie einen Registrierungseintrag für den Direktivenprozessor hinzu.  
  
 Sie müssen nur eine dieser Methoden verwenden, wenn Sie die Textvorlage in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] transformieren möchten.  Falls Sie in der Anwendung einen benutzerdefinierten Host verwenden, ist dieser für die Suche nach Direktivenprozessoren für die einzelnen Direktiven zuständig.  
  
## Bereitstellen eines Direktivenprozessors in einer VSIX  
 Sie können einer [Visual Studio\-Erweiterung \(VSIX\)](http://msdn.microsoft.com/de-de/64ff1452-f7d5-42d9-98b8-76f769f76832) einen benutzerdefinierten Direktivenprozessor hinzufügen.  
  
 Stellen Sie sicher, dass die VSIX\-Datei die folgenden zwei Elemente enthält:  
  
-   Die Assembly \(.dll\), die die benutzerdefinierte Direktivenprozessorklasse enthält.  
  
-   Eine PKGDEF\-Datei, durch die der Direktivenprozessor registriert wird.  Der Stammname der Datei muss mit dem Namen der Assembly identisch sein.  Die Dateinamen können z. B. "CDP.dll" und "CDP.pkgdef" lauten.  
  
 Wenn Sie den Inhalt einer VSIX\-Datei überprüfen oder ändern möchten, ändern Sie die Dateinamenerweiterung in .zip, und öffnen Sie die Datei dann.  Ändern Sie den Dateinamen wieder in .vsix, nachdem Sie den Inhalt bearbeitet haben.  
  
 Zum Erstellen einer VSIX\-Datei stehen mehrere Methoden zur Verfügung.  Im folgenden Verfahren wird eine Methode beschrieben.  
  
#### So entwickeln Sie einen benutzerdefinierten Direktivenprozessor in einem VSIX\-Projekt  
  
1.  Erstellen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein VSIX\-Projekt.  
  
    -   Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual Basic** oder **Visual C\#** und dann **Erweiterungen**.  Klicken Sie auf **VSIX Project**.  
  
2.  Legen Sie unter **source.extension.vsixmanifest** den Inhaltstyp und die unterstützten Editionen fest.  
  
    1.  Wählen Sie im VSIX\-Manifest\-Editor auf der Registerkarte **Objekte** die Option **Neu** aus, und legen Sie die Eigenschaften des neuen Elements fest:  
  
         **Inhaltstyp** \= **VSPackage**  
  
         **Quellprojekt** \= \<*the current project*\>  
  
    2.  Klicken Sie auf die Option für ausgewählte Editionen, und aktivieren Sie die Installationstypen, von denen der Direktivenprozessor unterstützt werden soll.  
  
3.  Fügen Sie eine PKGDEF\-Datei hinzu, und legen Sie die Eigenschaften fest, die in die VSIX eingeschlossen werden sollen.  
  
    1.  Erstellen Sie eine Textdatei mit dem Namen \<*assemblyName*\>.pkgdef.  
  
         \<*assemblyName*\> ist normalerweise identisch mit dem Projektnamen.  
  
    2.  Wählen Sie die Datei im Projektmappen\-Explorer aus, und legen Sie die Eigenschaften wie folgt fest:  
  
         **Buildvorgang** \= **Inhalt**  
  
         **In Ausgabeverzeichnis kopieren** \= **Immer kopieren**  
  
         **Include in VSIX** \= **True**  
  
    3.  Legen Sie den Namen der VSIX fest, und stellen Sie sicher, dass die ID eindeutig ist.  
  
4.  Fügen Sie der PKGDEF\-Datei den folgenden Text hinzu:  
  
    ```  
    [$RootKey$\TextTemplating]  
    [$RootKey$\TextTemplating\DirectiveProcessors]  
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]  
    @="Custom Directive Processor description"  
    "Class"="NamespaceName.ClassName"  
    "CodeBase"="$PackageFolder$\AssemblyName.dll"  
    ```  
  
     Ersetzen Sie die folgenden Namen durch eigene Namen: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.  
  
5.  Fügen Sie dem Projekt die folgenden Verweise hinzu:  
  
    -   **Microsoft.VisualStudio.TextTemplating.\*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.VSHost.\*.0**  
  
6.  Fügen Sie dem Projekt die benutzerdefinierte Direktivenprozessorklasse hinzu.  
  
     Dies ist eine öffentliche Klasse, die <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> oder <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementieren muss.  
  
#### So installieren Sie den benutzerdefinierten Direktivenprozessor  
  
1.  Öffnen Sie in Windows\-Explorer \(Datei\-Explor in Windows 8\) das Buildverzeichnis \(normalerweise "bin\\Debug" oder "bin\\Release"\).  
  
2.  Wenn Sie den Direktivenprozessor auf einem anderen Computer installieren möchten, kopieren Sie die VSIX\-Datei auf den anderen Computer.  
  
3.  Doppelklicken Sie auf die VSIX\-Datei.  Der Installer für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Erweiterungen wird angezeigt.  
  
4.  Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu.  Sie können jetzt Textvorlagen mit Direktiven ausführen, die auf den benutzerdefinierten Direktivenprozessor verweisen.  Jede Direktive besitzt das folgende Format:  
  
     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" … #>`  
  
#### So deinstallieren Sie den benutzerdefinierten Direktivenprozessor oder deaktivieren Sie ihn vorübergehend  
  
1.  Klicken Sie im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Menü **Extras** auf **Erweiterungs\-Manager**.  
  
2.  Wählen Sie die VSIX mit dem Direktivenprozessor aus, und klicken Sie dann auf **Deinstallieren** oder **Deaktivieren**.  
  
### Problembehandlung für einen Direktivenprozessor in einer VSIX  
 Die folgenden Hinweise können bei Problemen mit dem Direktivenprozessor hilfreich sein:  
  
-   Der in der benutzerdefinierten Direktive angegebene Prozessorname muss dem `CustomDirectiveProcessorName` entsprechen, den Sie in der PKGDEF\-Datei angegeben haben.  
  
-   Die `IsDirectiveSupported`\-Methode muss `true` zurückgeben, wenn der Name der `CustomDirective` an sie übergeben wird.  
  
-   Wenn die Erweiterung nicht im Erweiterungs\-Manager angezeigt wird, das System ihre Installation aber nicht zulässt, löschen Sie die Erweiterung aus **%localappdata%\\Microsoft\\VisualStudio\\\*.0\\Extensions\\**.  
  
-   Öffnen Sie die VSIX\-Datei, und überprüfen Sie den Inhalt.  Ändern Sie die Dateinamenerweiterung in .zip, um die Datei zu öffnen.  Vergewissern Sie sich, dass sie die DLL\-, PKGDEF\- und extension.vsixmanifest\-Dateien enthält.  Die extension.vsixmanifest\-Datei sollte die entsprechende Liste im Knoten "SupportedProducts" und einen Knoten "VsPackage" unter dem Knoten "Inhalt" enthalten:  
  
     `<Content>`  
  
     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`  
  
     `</Content>`  
  
## Bereitstellen eines Direktivenprozessors in einem VSPackage  
 Wenn der Direktivenprozessor Teil eines VSPackage ist, das im GAC installiert wird, können Sie die PKGDEF\-Datei vom System generieren lassen.  
  
 Fügen Sie das folgende Attribut in der Paketklasse ein:  
  
```  
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]  
```  
  
> [!NOTE]
>  Dieses Attribut wird in der Paketklasse eingefügt, nicht der Direktivenprozessorklasse.  
  
 Die PKGDEF\-Datei wird generiert, wenn Sie das Projekt erstellen.  Beim Installieren des VSPackage wird der Direktivenprozessor von der PKGDEF\-Datei registriert.  
  
 Überprüfen Sie, ob die PKGDEF\-Datei im Buildordner angezeigt wird \(normalerweise "bin\\Debug" oder "bin\\Release"\).  Falls sie nicht angezeigt wird, öffnen Sie die CSPROJ\-Datei in einem Text\-Editor, und entfernen Sie den folgenden Knoten: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`  
  
 Weitere Informationen finden Sie unter [VSPackages](../extensibility/internals/vspackages.md).  
  
## Festlegen eines Registrierungsschlüssels  
 Diese Methode zum Installieren eines benutzerdefinierten Direktivenprozessors wird am seltensten verwendet.  Bei dieser Methode ist das Aktivieren und Deaktivieren des Direktivenprozessors komplizierter, und der Direktivenprozessor kann nicht an andere Benutzer verteilt werden.  
  
> [!CAUTION]
>  Durch eine fehlerhafte Bearbeitung der Registrierung kann das System ernsthaft beschädigt werden.  Bevor Sie Änderungen an der Registrierung vornehmen, sollten Sie daher unbedingt alle wichtigen Daten auf dem Computer sichern.  
  
#### So registrieren Sie einen Direktivenprozessor durch Festlegen eines Registrierungsschlüssels  
  
1.  Führen Sie `regedit` aus.  
  
2.  Navigieren Sie in regedit zum folgenden Eintrag:  
  
     **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\\*.0\\TextTemplating\\DirectiveProcessors**  
  
     Wenn Sie den Direktivenprozessor in der Testversion von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren möchten, fügen Sie "Exp" nach "11.0" ein.  
  
3.  Fügen Sie einen Registrierungsschlüssel mit dem Namen der Direktivenprozessorklasse hinzu.  
  
    -   Klicken Sie in der Registrierungsstruktur mit der rechten Maustaste auf den Knoten **DirectiveProcessors**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Schlüssel**.  
  
4.  Fügen Sie im neuen Knoten entsprechend den folgenden Tabellen Zeichenfolgenwerte für "Class" und "CodeBase" oder "Assembly" hinzu.  
  
    1.  Klicken Sie mit der rechten Maustaste auf den von Ihnen erstellten Knoten, zeigen Sie auf **Neu**, und klicken Sie dann auf **Zeichenfolgenwert**.  
  
    2.  Bearbeiten Sie den Namen des Werts.  
  
    3.  Doppelklicken Sie auf den Namen, und bearbeiten Sie die Daten.  
  
 Wenn der benutzerdefinierte Direktivenprozessor nicht im GAC ist, sollten die Registrierungsunterschlüssel den Angaben in der folgenden Tabelle entsprechen:  
  
|Name|Typ|Daten|  
|----------|---------|-----------|  
|\(Standard\)|REG\_SZ|\(Wert nicht festgelegt\)|  
|Klasse|REG\_SZ|\<Namespacename\>.\<Klassenname\>|  
|CodeBase|REG\_SZ|\<Ihr Pfad\>\\\<Ihr Assemblyname\>|  
  
 Wenn die Assembly im GAC ist, sollten die Registrierungsunterschlüssel den Angaben in der folgenden Tabelle entsprechen:  
  
|Name|Typ|Daten|  
|----------|---------|-----------|  
|\(Standard\)|REG\_SZ|\(Wert nicht festgelegt\)|  
|Klasse|REG\_SZ|\<Ihr vollqualifizierter Klassenname\>|  
|Assembly|REG\_SZ|\<Ihr Assemblyname im GAC\>|  
  
## Siehe auch  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)