---
title: Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dcb562eb76e13b5dcb16532ed808b2447de0d6c8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778409"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Für die einfache Erstellung eines Elements oder einer Gruppe von Elementen gemäß eines Musters, das Sie häufig verwenden, können Sie der Toolbox mit Modellierungsdiagrammen in Visual Studio neue Tools hinzufügen. Sie können diese Toolboxelemente an andere Visual Studio-Benutzer verteilen.  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Ein benutzerdefiniertes Tool erstellt ein oder mehrere neue Elemente in einem Diagramm. Sie können z. B. ein benutzerdefiniertes Tool zum Erstellen von Elementen, wie beispielsweise die folgenden, erstellen:  
  
-   Ein Paket, das mit dem .NET-Profil verknüpft ist, und eine Klasse mit dem .NET-Stereotyp.  
  
-   Ein Paar von Klassen, das durch eine Zuordnung verknüpft ist, um das Observer-Muster darzustellen.  
  
> [!NOTE]
>  Sie können diese Methode verwenden, um Elementtools zu erstellen. Das heißt, Sie können Tools erstellen, die Sie aus der Toolbox in ein Diagramm ziehen. Sie können keine Connector-Tools erstellen.  
  
##  <a name="DefineTool"></a> Definieren ein benutzerdefinierten Modellierungstools  
  
#### <a name="to-define-a-custom-modeling-tool"></a>So definieren Sie ein benutzerdefiniertes Modellierungstool  
  
1.  Erstellen Sie ein UML-Diagramm, das ein Element oder eine Gruppe von Elementen enthält.  
  
    -   Diese Elemente können Beziehungen untereinander haben und untergeordnete Elemente wie Ports, Attribute, Vorgänge oder Pins aufweisen.  
  
2.  Speichern Sie das Diagramm mit dem Namen, den das neue Tool erhalten soll. Auf der **Datei** Menü **speichern... Als**.  
  
3.  Kopieren Sie mithilfe von Windows-Explorer die zwei Diagrammdateien in den folgenden Ordner oder einen beliebigen Unterordner:  
  
     *YourDocuments* **\Visual Studio\Architecture Tools\Custom Toolboxelemente**  
  
    -   Erstellen Sie diesen Ordner, wenn er nicht bereits vorhanden ist. Möglicherweise müssen Sie beide erstellen **Architekturtools** und **benutzerdefinierte Toolboxelemente**.  
  
    -   Kopieren Sie beide Diagrammdateien, eine mit einem Namen, der endet "... **Diagramm**"und der andere mit einem Namen, die endet"... **diagram.layout**"  
  
    -   Sie können beliebig viele benutzerdefinierte Tools erstellen. Verwenden Sie ein Diagramm für jedes Tool.  
  
4.  (Optional) Erstellen Sie eine **tbxinfo** Datei wie in beschrieben [Gewusst wie: Definieren der Eigenschaften des benutzerdefinierten Tools](#tbxinfo), und fügen Sie es in dasselbe Verzeichnis. Auf diese Weise können Sie ein Toolboxsymbol, eine QuickInfo usw. definieren.  
  
    -   Ein einzelnes **tbxinfo** Datei zum Definieren mehrerer Tools verwendet werden kann. Diese kann auf Diagrammdateien verweisen, die sich in Unterordnern befinden.  
  
5.  Starten Sie Visual Studio neu. Das zusätzliche Tool wird in der Toolbox für den entsprechenden Diagrammtyp angezeigt.  
  
### <a name="what-the-custom-tool-will-replicate"></a>Was vom benutzerdefinierten Tool repliziert wird  
 Ein benutzerdefiniertes Tool repliziert die meisten Funktionen des Quelldiagramms:  
  
- Namen Wenn ein Element aus der Toolbox erstellt wird, wird bei Bedarf eine Zahl am Ende des Namens hinzugefügt, um doppelte Namen im selben Namespace zu verhindern.  
  
- Farben, Größen und Formen  
  
- Stereotype und Paketprofile  
  
- Eigenschaftswerte wie z. B. Is Abstract  
  
- Verknüpfte Arbeitsaufgaben  
  
- Multiplizitäten und andere Eigenschaften von Beziehungen  
  
- Die relativen Positionen von Formen  
  
  Die folgenden Funktionen werden in einem benutzerdefinierten Tool nicht beibehalten:  
  
- Einfache Formen Hierbei handelt es sich um Formen, die nicht im Zusammenhang mit Modellelementen stehen, die Sie in einigen Arten von Diagrammen zeichnen können.  
  
- Connector-Routing Wenn Sie Connectors manuell weiterleiten, wird das Routing nicht beibehalten, wenn das Tool verwendet wird. Die Positionen einiger geschachtelter Formen, wie z. B. Ports, werden in Bezug auf ihre Besitzer nicht beibehalten.  
  
##  <a name="tbxinfo"></a> Gewusst wie: Definieren Sie die Eigenschaften des benutzerdefinierten Tools  
 Einer Toolboxinformationsdatei (**tbxinfo**) Datei können Sie geben Sie einen Toolboxnamen, die Symbol, die QuickInfo, die Registerkarte, und ein Hilfeschlüsselwort für ein oder mehrere benutzerdefinierte Tools. Geben sie einen beliebigen Namen, wie z. B. **MyTools.tbxinfo**.  
  
 Die allgemeine Form der Datei ist wie folgt:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">  
  <customToolboxItem fileName="MyObserverTool.classdiagram">  
    <displayName>  
       <value>Observer Pattern</value>  
    </displayName>  
    <tabName>  
       <value>UML Class Diagram</value>  
    </tabName>  
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>  
    <f1Keyword>  
      <value>ObserverPatternHelp</value>  
    </f1Keyword>  
    <tooltip>  
       <value>Create a pair of classes</value>  
    </tooltip>  
  </customToolboxItem>  
</customToolboxItems>  
```  
  
 Der Wert jedes Elements kann Folgendes sein:  
  
- `<bmp fileName="…"/>` für das Toolboxsymbol und `<value>string</value>` für die anderen Elemente, wie in dem Beispiel dargestellt.  
  
  \- oder –  
  
- `<resource fileName="Resources.dll"`  
  
   `baseName="Observer.resources" id="Observer.tabname" />`  
  
   In diesem Fall geben Sie eine kompilierte Assembly an, in der die Zeichenfolgenwerte als Ressourcen kompiliert wurden.  
  
  Fügen Sie einen `<customToolboxItem>`-Knoten für jedes Toolboxelement hinzu, das Sie definieren möchten.  
  
  Die Knoten in der **tbxinfo** -Datei sind wie folgt. Es gibt einen Standardwert für jeden Knoten.  
  
|Knotenname|Definiert|  
|---------------|-------------|  
|displayName|Der Name des Toolboxelements.|  
|tabName|Die Toolboxregisterkarte, in der das Element angezeigt werden soll. Sie können entweder den Namen der normalen Registerkarte für diesen Typ von Diagramm oder einen anderen Namen angeben.|  
|Bild|Der Speicherort der Bitmap (**BMP**)-Datei, die Höhe und Breite von 16 Bit und eine Farbtiefe von 24 Bit aufweisen muss.|  
|f1Keyword|Das Schlüsselwort, mit dem ein Hilfethema gesucht wird.|  
|QuickInfo|Eine QuickInfo für dieses Tool.|  
  
 Sie können die Bitmapdatei in Visual Studio bearbeiten und ihre Höhe und Breite im Eigenschaftenfenster auf 16 festlegen.  
  
> [!NOTE]
>  Wenn Sie beginnen, eine TBXINFO-Datei zu verwenden, nachdem Sie mit der alleinigen Verwendung von Diagrammdateien experimentiert haben, stellen sie möglicherweise fest, dass die Toolbox sowohl die alten als auch die neuen Versionen eines Toolboxelements enthält. Dies kann auch auftreten, wenn der Name der Diagrammdatei in der TBXINFO-Datei falsch eingegeben wurde. Wählen Sie in diesem Fall auf das Kontextmenü der Toolbox **Toolbox zurücksetzen**. Die benutzerdefinierten Toolboxelemente werden ausgeblendet. Starten Sie Visual Studio neu; daraufhin werden die richtigen benutzerdefinierten Elemente angezeigt.  
  
##  <a name="Extension"></a> Gewusst wie: Verteilen von Toolboxelementen in Visual Studio-Erweiterung  
 Sie können Toolboxelemente an andere verteilen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Benutzer, indem Sie sie in einem Visual Studio-Erweiterung (VSIX) verpacken. Sie können Befehle, Profile und andere Erweiterungen in der gleichen VSIX-Datei verpacken. Weitere Informationen finden Sie unter [Bereitstellen von Visual Studio-Erweiterungen](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
 Die übliche Vorgehensweise zum Erstellen einer Visual Studio-Erweiterung besteht darin, die VSIX-Projektvorlage zu verwenden. Zu diesem Zweck muss [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] installiert sein.  
  
#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>So fügen Sie ein Toolboxelement zu einer Visual Studio-Erweiterung hinzu  
  
1.  [Erstellen und Testen Sie eine oder mehrere benutzerdefinierte Tools](#DefineTool).  
  
2.  [Erstellen Sie eine tbxinfo-Datei](#tbxinfo) , die auf die Tools verweist.  
  
3.  Öffnen Sie ein vorhandenes Visual Studio-Erweiterungsprojekt.  
  
     \- oder –  
  
     Definieren Sie ein neues Visual Studio-Erweiterungsprojekt.  
  
    1.  Wählen Sie im Menü **Datei** die Optionsfolge **Neu**, **Projekt**aus.  
  
    2.  In der **neues Projekt** Dialogfeld **installierte Vorlagen**, wählen Sie **Visual C#-**, **Erweiterbarkeit**, **VSIX Projekt**.  
  
4.  Fügen Sie die Toolboxdefinitionen dem Projekt hinzu. Enthalten die **tbxinfo** -Datei, die Diagrammdateien, Bitmapdateien und alle Ressourcendateien ein, und stellen Sie sicher, dass sie in die VSIX-Datei enthalten sind.  
  
    -   Wählen Sie im Projektmappen-Explorer auf das Kontextmenü des VSIX-Projekts **hinzufügen**, **vorhandenes Element**. Klicken Sie im Dialogfeld festlegen **Objekttyp: alle Dateien**. Suchen Sie die Dateien, wählen sie alle aus, und wählen Sie dann **hinzufügen**.  
  
        > [!NOTE]
        >  In diesem Projekt können die Diagrammdateien nicht im Modell-Editor geöffnet werden.  
  
5.  Legen Sie die folgenden Eigenschaften aller Dateien fest, die Sie gerade hinzugefügt haben. Sie können ihre Eigenschaften gleichzeitig festlegen, indem Sie alle im Projektmappen-Explorer auswählen. Achten Sie darauf, dass Sie keine Änderungen an den Eigenschaften der anderen Dateien im Projekt vornehmen.  
  
     **In Ausgabeverzeichnis kopieren** = **immer kopieren**  
  
     **Buildvorgang** = **Inhalt**  
  
     **In VSIX einbeziehen** = **"true"**  
  
6.  Öffnen Sie **source.extension.vsixmanifest**. Die Datei wird im Erweiterungsmanifest-Editor geöffnet.  
  
7.  Klicken Sie unter **Metadaten**, fügen Sie eine Beschreibung für die benutzerdefinierten Tools hinzu.  
  
     Klicken Sie unter **Assets**, wählen Sie **neu** und legen Sie dann die Felder im Dialogfeld wie folgt:  
  
    -   **Typ** = **benutzerdefinierte Erweiterungstyp**  
  
    -   Typ = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`  
  
        > [!NOTE]
        >  Dies ist keine der Optionen in der Dropdownliste. Sie müssen sie über die Tastatur eingeben.  
  
    -   **Quelle** = **Datei im Dateisystem**.  
  
    -   **Pfad** = Ihre **tbxinfo** -Datei, z. B. **MyTools.tbxinfo**  
  
8.  Erstellen Sie das Projekt.  
  
9. **Um sicherzustellen, dass die Erweiterung funktioniert**, drücken Sie F5. Die experimentelle Instanz von Visual Studio wird geöffnet.  
  
     Erstellen oder öffnen Sie in der experimentellen Instanz ein UML-Diagramm des relevanten Typs. Stellen Sie sicher, dass das neue Tool in der Toolbox angezeigt wird und dass Elemente ordnungsgemäß erstellt werden.  
  
10. **Um eine VSIX-Datei für die Bereitstellung zu erhalten:** öffnen Sie im Windows-Explorer den Ordner **.\bin\Debug** oder **.\bin\Release** finden die **VSIX** Datei. Dies ist eine [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Erweiterungsdatei. Sie kann auf dem Computer installiert und an andere Visual Studio-Benutzer gesendet werden.  
  
#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>So installieren Sie benutzerdefinierte Tools aus einer Visual Studio-Erweiterung  
  
1.  Öffnen Sie im Windows-Explorer oder in Visual Studio die `.vsix`-Datei.  
  
2.  Wählen Sie **installieren** im Dialogfeld, das angezeigt wird.  
  
3.  Öffnen Sie zum Deinstallieren oder vorübergehend deaktivieren Sie die Erweiterung, **Erweiterungen und Updates** aus der **Tools** Menü.  
  
## <a name="localization"></a>Lokalisierung  
 Sie können eine Erweiterung erstellen, die bei der Installation auf einem anderen Computer Toolnamen und QuickInfos in der Sprache des Zielcomputers anzeigt.  
  
#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>So stellen Sie Versionen des Tools in mehreren Sprachen bereit  
  
1. Erstellen Sie ein Visual Studio-Erweiterungsprojekt, das ein oder mehrere benutzerdefinierte Tools enthält.  
  
    In der **tbxinfo** Datei, verwenden Sie zum Definieren des Tools Ressourcendateimethode `displayName`, Toolbox `tabName`, und der QuickInfo. Erstellen Sie eine Ressourcendatei, in der diese Zeichenfolgen definiert sind, kompilieren Sie diese in eine Assembly, und verweisen Sie dann aus der TBXINFO-Datei darauf.  
  
2. Erstellen Sie zusätzliche Assemblys, die Ressourcendateien mit Zeichenfolgen in anderen Sprachen enthalten.  
  
3. Legen Sie jede zusätzliche Assembly in einen Ordner, dessen Name der Kulturcode für die Sprache ist. Platzieren Sie z. B. eine französische Version der Assembly in einen Ordner mit dem Namen **"fr"**.  
  
4. Sie sollten einen neutralen Kulturcode verwenden, also in der Regel zwei Buchstaben. Verwenden Sie keine speziellen Kulturcodes wie `fr-CA`. Weitere Informationen zu kulturcodes finden Sie unter [CultureInfo.GetCultures-Methode](http://go.microsoft.com/fwlink/?LinkId=160782), die eine vollständige Liste der kulturcodes bereitstellt.  
  
5. Erstellen Sie die Visual Studio-Erweiterung, und verteilen Sie sie.  
  
6. Wenn die Erweiterung auf einem anderen Computer installiert ist, wird die Version der Ressourcendatei für die lokale Kultur des Benutzers automatisch geladen. Wenn Sie keine Version für die Kultur des Benutzers angegeben haben, werden die Standardressourcen verwendet.  
  
   Sie können diese Methode verwenden, um verschiedene Versionen des Prototypdiagramms zu installieren. Die Namen von Elementen und Connectors sind in jeder Installation identisch.  
  
## <a name="other-toolbox-operations"></a>Andere Toolboxvorgänge  
 In [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] können Sie normalerweise die Toolbox anpassen, indem Sie Tools umbenennen, diese in andere Toolboxregisterkarten verschieben und löschen. Aber diese Änderungen werden für benutzerdefinierte Modellierungstools, die mit den in diesem Thema beschriebenen Verfahren erstellt wurden, nicht beibehalten. Beim Neustart von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] werden benutzerdefinierte Tools wieder mit ihren definierten Namen und Toolboxspeicherorten angezeigt.  
  
 Die benutzerdefinierten Tools ausgeblendet, wenn Sie beim Ausführen der **Toolbox zurücksetzen** Befehl. Sie werden jedoch wieder angezeigt, wenn Sie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] neu starten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)   
 [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definieren von Validierungseinschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md)



