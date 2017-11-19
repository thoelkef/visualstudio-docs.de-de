---
title: Bereitstellen eines benutzerdefinierten Direktivenprozessors | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, custom directive processors
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: f020dbd8aef022acaafe0561fba11343e9272ff6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="deploying-a-custom-directive-processor"></a>Bereitstellen eines benutzerdefinierten Anweisungsprozessors
Wenn Sie auf einem Computer einen benutzerdefinierten Direktivenprozessor in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwenden möchten, müssen Sie ihn anhand einer der in diesem Thema beschriebenen Methoden registrieren.  
  
 Folgende Methoden stehen zur Auswahl:  
  
-   [Visual Studio-Erweiterung (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832). Ermöglicht die Installation und Deinstallation des Anweisungsprozessors auf dem eigenen Computer und anderen Computern. Normalerweise können weitere Funktionen in der gleichen VSIX gebündelt werden.  
  
-   [VSPackage](../extensibility/internals/vspackages.md). Wenn Sie ein VSPackage definieren, das neben dem Direktivenprozessor weitere Funktionen enthält, kann der Direktivenprozessor einfach registriert werden.  
  
-   Festlegen eines Registrierungsschlüssels. Bei dieser Methode fügen Sie einen Registrierungseintrag für den Direktivenprozessor hinzu.  
  
 Sie müssen nur eine dieser Methoden verwenden, wenn Sie die Textvorlage in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] transformieren möchten. Falls Sie in der Anwendung einen benutzerdefinierten Host verwenden, ist dieser für die Suche nach Direktivenprozessoren für die einzelnen Direktiven zuständig.  
  
## <a name="deploying-a-directive-processor-in-a-vsix"></a>Bereitstellen eines Anweisungsprozessors in einer VSIX  
 Sie können einen benutzerdefinierten Direktivenprozessor Hinzufügen einer [Visual Studio-Erweiterung (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832).  
  
 Stellen Sie sicher, dass die VSIX-Datei die folgenden zwei Elemente enthält:  
  
-   Die Assembly (.dll), die die benutzerdefinierte Direktivenprozessorklasse enthält.  
  
-   Eine PKGDEF-Datei, durch die der Direktivenprozessor registriert wird. Der Stammname der Datei muss mit dem Namen der Assembly identisch sein. Die Dateinamen können z. B. "CDP.dll" und "CDP.pkgdef" lauten.  
  
 Wenn Sie den Inhalt einer VSIX-Datei überprüfen oder ändern möchten, ändern Sie die Dateinamenerweiterung in .zip, und öffnen Sie die Datei dann. Ändern Sie den Dateinamen wieder in .vsix, nachdem Sie den Inhalt bearbeitet haben.  
  
 Zum Erstellen einer VSIX-Datei stehen mehrere Methoden zur Verfügung. Im folgenden Verfahren wird eine Methode beschrieben.  
  
#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>So entwickeln Sie einen benutzerdefinierten Direktivenprozessor in einem VSIX-Projekt  
  
1.  Erstellen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein VSIX-Projekt.  
  
    -   In der **neues Projekt** Dialogfeld erweitern Sie **Visual Basic** oder **Visual C#-**, erweitern Sie dann **Erweiterbarkeit**. Klicken Sie auf **VSIX-Projekt**.  
  
2.  In **"Source.Extension.vsixmanifest"**, legen Sie den Inhaltstyp und die unterstützten Editionen.  
  
    1.  In VSIX-manifest-Editor auf die **Bestand** Registerkarte **neu** und Festlegen von Eigenschaften für das neue Element:  
  
         **Inhaltstyp** = **VSPackage**  
  
         **Quellprojekt** = \<*des aktuellen Projekts*>  
  
    2.  Klicken Sie auf **ausgewählte Editionen** und überprüfen Sie die Installationstypen, von der Direktivenprozessor verwendet werden soll.  
  
3.  Fügen Sie eine PKGDEF-Datei hinzu, und legen Sie die Eigenschaften fest, die in die VSIX eingeschlossen werden sollen.  
  
    1.  Erstellen Sie eine Textdatei, und nennen Sie sie \< *AssemblyName*> PKGDEF.  
  
         \<*AssemblyName*> ist in der Regel identisch mit den Namen des Projekts.  
  
    2.  Wählen Sie die Datei im Projektmappen-Explorer aus, und legen Sie die Eigenschaften wie folgt fest:  
  
         **Buildvorgang** = **Inhalt**  
  
         **In Ausgabeverzeichnis kopieren** = **immer kopieren**  
  
         **In VSIX einbeziehen** = **"true"**  
  
    3.  Legen Sie den Namen der VSIX fest, und stellen Sie sicher, dass die ID eindeutig ist.  
  
4.  Fügen Sie der PKGDEF-Datei den folgenden Text hinzu:  
  
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
  
    -   **Microsoft.VisualStudio.TextTemplating. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.VSHost. \*.0**  
  
6.  Fügen Sie dem Projekt die benutzerdefinierte Anweisungsprozessorklasse hinzu.  
  
     Dies ist eine öffentliche Klasse, die <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> oder <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementieren muss.  
  
#### <a name="to-install-the-custom-directive-processor"></a>So installieren Sie den benutzerdefinierten Direktivenprozessor  
  
1.  Öffnen Sie in Windows-Explorer (Datei-Explor in Windows 8) das Buildverzeichnis (normalerweise "bin\Debug" oder "bin\Release").  
  
2.  Wenn Sie den Direktivenprozessor auf einem anderen Computer installieren möchten, kopieren Sie die VSIX-Datei auf den anderen Computer.  
  
3.  Doppelklicken Sie auf die VSIX-Datei. Der Installer für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Erweiterungen wird angezeigt.  
  
4.  Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu. Sie können jetzt Textvorlagen mit Direktiven ausführen, die auf den benutzerdefinierten Direktivenprozessor verweisen. Jede Anweisung besitzt das folgende Format:  
  
     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`  
  
#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>So deinstallieren Sie den benutzerdefinierten Anweisungsprozessor oder deaktivieren Sie ihn vorübergehend  
  
1.  In der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Tools** Menü klicken Sie auf **Erweiterungs-Manager**.  
  
2.  Wählen Sie die VSIX mit dem Direktivenprozessor aus, und klicken Sie dann auf **Deinstallieren** oder **deaktivieren**.  
  
### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Problembehandlung für einen Anweisungsprozessor in einer VSIX  
 Die folgenden Hinweise können bei Problemen mit dem Direktivenprozessor hilfreich sein:  
  
-   Der in der benutzerdefinierten Direktive angegebene Prozessorname muss dem `CustomDirectiveProcessorName` entsprechen, den Sie in der PKGDEF-Datei angegeben haben.  
  
-   Die `IsDirectiveSupported`-Methode muss `true` zurückgeben, wenn der Name der `CustomDirective` an sie übergeben wird.  
  
-   Wenn die Erweiterung im Erweiterungs-Manager nicht angezeigt, aber das System nicht lässt, es installieren, löschen Sie die Erweiterung von **%localappdata%\Microsoft\VisualStudio\\\*. 0\Extensions\\** .  
  
-   Öffnen Sie die VSIX-Datei, und überprüfen Sie den Inhalt. Ändern Sie die Dateinamenerweiterung in .zip, um die Datei zu öffnen. Vergewissern Sie sich, dass sie die DLL-, PKGDEF- und extension.vsixmanifest-Dateien enthält. Die extension.vsixmanifest-Datei sollte die entsprechende Liste im Knoten "SupportedProducts" und einen Knoten "VsPackage" unter dem Knoten "Inhalt" enthalten:  
  
     `<Content>`  
  
     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`  
  
     `</Content>`  
  
## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Bereitstellen eines Anweisungsprozessors in einem VSPackage  
 Wenn der Direktivenprozessor Teil eines VSPackage ist, das im GAC installiert wird, können Sie die PKGDEF-Datei vom System generieren lassen.  
  
 Fügen Sie das folgende Attribut in der Paketklasse ein:  
  
```  
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]  
```  
  
> [!NOTE]
>  Dieses Attribut wird in der Paketklasse eingefügt, nicht der Direktivenprozessorklasse.  
  
 Die PKGDEF-Datei wird generiert, wenn Sie das Projekt erstellen. Beim Installieren des VSPackage wird der Direktivenprozessor von der PKGDEF-Datei registriert.  
  
 Überprüfen Sie, ob die PKGDEF-Datei im Buildordner angezeigt wird (normalerweise "bin\Debug" oder "bin\Release"). Falls sie nicht angezeigt wird, öffnen Sie die CSPROJ-Datei in einem Text-Editor, und entfernen Sie den folgenden Knoten: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`  
  
 Weitere Informationen finden Sie unter [VSPackages](../extensibility/internals/vspackages.md).  
  
## <a name="setting-a-registry-key"></a>Festlegen eines Registrierungsschlüssels  
 Diese Methode zum Installieren eines benutzerdefinierten Direktivenprozessors wird am seltensten verwendet. Bei dieser Methode ist das Aktivieren und Deaktivieren des Direktivenprozessors komplizierter, und der Direktivenprozessor kann nicht an andere Benutzer verteilt werden.  
  
> [!CAUTION]
>  Durch eine fehlerhafte Bearbeitung der Registrierung kann das System ernsthaft beschädigt werden. Bevor Sie Änderungen an der Registrierung vornehmen, sollten Sie daher unbedingt alle wichtigen Daten auf dem Computer sichern.  
  
#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>So registrieren Sie einen Anweisungsprozessor durch Festlegen eines Registrierungsschlüssels  
  
1.  Führen Sie `regedit` aus.  
  
2.  Navigieren Sie in regedit zum folgenden Eintrag:  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  
  
     Wenn Sie den Direktivenprozessor in der Testversion von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren möchten, fügen Sie "Exp" nach "11.0" ein.  
  
3.  Fügen Sie einen Registrierungsschlüssel mit dem Namen der Anweisungsprozessorklasse hinzu.  
  
    -   In der Registrierungsstruktur mit der Maustaste die **DirectiveProcessors** Knoten, zeigen Sie auf **neu**, und klicken Sie dann auf **Schlüssel**.  
  
4.  Fügen Sie im neuen Knoten entsprechend den folgenden Tabellen Zeichenfolgenwerte für "Class" und "CodeBase" oder "Assembly" hinzu.  
  
    1.  Mit der rechten Maustaste des Knotens, die Sie erstellt haben, zeigen Sie auf **neu**, und klicken Sie dann auf **Zeichenfolgenwert**.  
  
    2.  Bearbeiten Sie den Namen des Werts.  
  
    3.  Doppelklicken Sie auf den Namen, und bearbeiten Sie die Daten.  
  
 Wenn der benutzerdefinierte Direktivenprozessor nicht im GAC ist, sollten die Registrierungsunterschlüssel den Angaben in der folgenden Tabelle entsprechen:  
  
|Name|Typ|Daten|  
|----------|----------|----------|  
|(Standard)|REG_SZ|(Wert nicht festgelegt)|  
|Klasse|REG_SZ|**\<Namespace-Name >. \<Klassenname >**|  
|CodeBase|REG_SZ|**\<Ihr Pfad >\\< Ihr Assemblyname\>**|  
  
 Wenn die Assembly im GAC ist, sollten die Registrierungsunterschlüssel den Angaben in der folgenden Tabelle entsprechen:  
  
|Name|Typ|Daten|  
|----------|----------|----------|  
|(Standard)|REG_SZ|(Wert nicht festgelegt)|  
|Klasse|REG_SZ|\<**Der vollqualifizierte Klassenname**>|  
|Assembly|REG_SZ|\<**Der Name der Assembly im globalen Assemblycache**>|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von benutzerdefinierten T4-Anweisungsprozessoren für Textvorlagen](../modeling/creating-custom-t4-text-template-directive-processors.md)