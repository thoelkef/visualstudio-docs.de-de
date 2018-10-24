---
title: Definieren eines Profils zum Erweitern von UML | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2886e454e9986e63cbc3496d3ef5b0664e85dede
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851594"
---
# <a name="define-a-profile-to-extend-uml"></a>Definieren eines Profils zum Erweitern von UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können definieren, eine *UML-Profil* auf die standardmäßigen Modellelemente für bestimmte Zwecke anzupassen. Ein Profil definiert eine oder mehrere *UML-Stereotype*. Ein Stereotyp kann verwendet werden, um einen Typ als Darstellung einer bestimmten Art Objekt zu markieren. Ein Stereotyp kann außerdem verwendet werden, um die Liste der Eigenschaften eines Elements zu erweitern.  
  
 Mehrere Profile werden mit unterstützten Editionen von Visual Studio installiert. Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Weitere Informationen zu diesen Profilen und zur Anwendung von Stereotypen finden Sie unter [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
 Sie können eigene Profile definieren, um UML an Ihren eigenen Geschäftsbereich oder Ihre Architektur anzupassen und bei Bedarf zu erweitern. Zum Beispiel:  
  
- Wenn Sie häufig Websites definieren, können Sie ein eigenes Profil definieren, das ein Stereotyp "Webseite" bereitstellt, das in Klassendiagrammen auf Klassen angewendet werden kann. Sie können mithilfe von Klassendiagrammen dann eine Website planen. Jede "Webseite"-Klasse enthält zusätzliche Eigenschaften für Seiteninhalt, Format usw.  
  
- Wenn Sie Banksoftware entwickeln, können Sie ein Profil definieren, das ein "Konto"-Stereotyp bereitstellt. Sie können dann Klassendiagramme verwenden, um andere Kontotypen zu definieren und die Beziehungen zwischen ihnen anzuzeigen.  
  
  Sie können eigene Profile an das Team verteilen. Jedes Teammitglied kann das Profil installieren. Auf diese Weise können die Teammitglieder Modelle bearbeiten und erstellen, die die Stereotype verwenden.  
  
> [!NOTE]
>  Wenn Sie die Stereotype eines Profils in einem Modell anwenden, das Sie bearbeiten, und das Modell dann für andere Personen freigeben, sollten diese Personen auf ihren Computern das gleiche Profil installieren. Andernfalls sind sie nicht in der Lage, die Stereotype anzuzeigen, die Sie verwendet haben.  
  
 Ein Profil ist häufig Teil einer größeren [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Erweiterung. Sie können z. B. einen Befehl definieren, der einige Teile eines Modells in Code übersetzt. Sie können ein Profil definieren, das Benutzer auf Pakete anwenden müssen, die sie übersetzen möchten. In diesem Fall verteilen Sie den neuen Befehl gemeinsam mit dem Profil in einer einzelnen [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Erweiterung.  
  
 Sie können auch lokalisierte Varianten eines Profils definieren. Benutzer, die die Erweiterung laden, sehen die Variante, die für ihre eigene Kultur geeignet ist.  
  
##  <a name="DefineProfile"></a> Gewusst wie: Definieren eines Profils  
  
#### <a name="to-define-a-uml-profile"></a>So definieren Sie ein UML-Profil  
  
1.  Erstellen Sie eine neue XML-Datei mit der Dateierweiterung `.profile`.  
  
2.  Fügen Sie Stereotypdefinitionen gemäß den Richtlinien unter [die Struktur eines Profils](#Schema).  
  
3.  Fügen Sie das Profil einer Visual Studio-Erweiterung hinzu (`.vsix`-Datei). Sie können entweder eine neue Erweiterung für das Profil erstellen oder dem Profil eine vorhandene Erweiterung hinzufügen.  
  
     Im nächsten Abschnitt, [Gewusst wie: Hinzufügen eines Profils zu einer Visual Studio-Erweiterung](#AddProfile).  
  
4.  Installieren Sie die Erweiterung auf dem Computer.  
  
    1.  Doppelklicken Sie auf die Erweiterungsdatei mit der Dateinamenerweiterung `.vsix`.  
  
    2.  Starten Sie Visual Studio neu.  
  
5.  Überprüfen Sie, ob das Profil installiert wurde.  
  
    1.  Wählen Sie das Modell in UML-Explorer aus.  
  
    2.  Klicken Sie im Eigenschaftenfenster auf die **Profile** Eigenschaft. Das Profil wird im Menü angezeigt. Setzen Sie das Häkchen neben dem Profil.  
  
    3.  Wählen Sie ein Element aus, für welches das Profil Stereotype definiert. Klicken Sie im Eigenschaftenfenster auf die **Stereotype** Eigenschaft. Die Stereotype werden in der Liste aufgeführt. Setzen bei einem der Stereotype ein Häkchen.  
  
    4.  Wenn das Profil zusätzliche Eigenschaften für dieses Stereotyp definiert, erweitern Sie die Stereotypeigenschaft, um sie anzuzeigen.  
  
6.  Senden Sie die Erweiterungsdatei an andere Benutzer von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], damit diese sie auf ihren Computern installieren können.  
  
##  <a name="AddProfile"></a> Gewusst wie: Hinzufügen eines Profils zu einer Visual Studio-Erweiterung  
 Um ein Profil zu installieren und das Senden an andere Benutzer zu ermöglichen, müssen Sie das Profil einer Visual Studio-Erweiterung hinzufügen. Weitere Informationen finden Sie unter [Bereitstellen von Visual Studio-Erweiterungen](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>So definieren Sie ein Profil in einer neuen Visual Studio-Erweiterung  
  
1. Erstellen Sie ein Visual Studio-Erweiterungsprojekt.  
  
   > [!NOTE]
   >  Um dieses Verfahren durchführen zu können, muss [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] installiert sein.  
  
   1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
   2.  In der **neues Projekt** Dialogfeld **installierte Vorlagen**, erweitern Sie **Visual C#-**, klicken Sie auf **Erweiterbarkeit**, und klicken Sie dann auf  **VSIX-Projekt**. Legen Sie den Namen des Projekts, und klicken Sie auf **OK**.  
  
2. Fügen Sie das Profil dem Projekt hinzu.  
  
   -   Klicken Sie im Projektmappen-Explorer mit der Maustaste des Projekts, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **vorhandenes Element**. Suchen Sie im Dialogfeld nach der Profildatei.  
  
3. Legen Sie der Profildatei **in Ausgabeverzeichnis kopieren** Eigenschaft.  
  
   1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in der Profildatei, und klicken Sie dann auf **Eigenschaften**.  
  
   2.  Legen Sie im Fenster Eigenschaften die **in Ausgabeverzeichnis kopieren** Eigenschaft **immer kopieren**.  
  
4. Öffnen Sie im Projektmappen-Explorer die Erweiterung `source.extension.vsixmanifest`.  
  
    Die Datei wird im Erweiterungsmanifest-Editor geöffnet.  
  
5. Auf der **Assets** Seite, fügen Sie eine Zeile, die das Profil beschreibt:  
  
   -   Klicken Sie auf **neue**. Legen Sie die Felder in der **neue Anlage hinzufügen** Dialogfeld wie folgt.  
  
   -   Legen Sie **Typ** auf `Microsoft.VisualStudio.UmlProfile`  
  
        Dies ist keine der Dropdown-Auswahlmöglichkeiten. Geben Sie diesen Namen über die Tastatur ein.  
  
   -   Klicken Sie auf **Datei im Dateisystem** , und wählen Sie den Namen der Profildatei aus, z. B. `MyProfile.profile`  
  
6. Erstellen Sie das Projekt.  
  
7. **So debuggen Sie das Profil**, drücken Sie F5.  
  
    Eine experimentelle Instanz von Visual Studio wird geöffnet. Öffnen Sie in dieser Instanz ein Modellierungsprojekt. Wählen Sie im UML-Explorer das Stammelement des Modells und im Eigenschaftenfenster das Profil aus. Wählen Sie dann Elemente innerhalb der Modell- und Satzstereotypen aus, die Sie dafür definiert haben.  
  
8. **Extrahieren Sie VSIX für die Bereitstellung**  
  
   1.  Öffnen Sie im Windows-Explorer den Ordner **.\bin\Debug** oder **.\bin\Release** finden die **VSIX** Datei. Dies ist eine [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Erweiterungsdatei. Sie kann auf dem Computer installiert und an andere Visual Studio-Benutzer gesendet werden.  
  
   2.  So installieren Sie die Erweiterung:  
  
       1.  Doppelklicken Sie auf die `.vsix`-Datei. Der Installer für Visual Studio-Erweiterungen wird gestartet.  
  
       2.  Starten Sie alle Instanzen von Visual Studio neu, die ausgeführt werden.  
  
   Sie können das folgende alternative Verfahren für kleine Erweiterungen verwenden, falls Sie [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] nicht installiert haben.  
  
#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>So definieren Sie eine Profilerweiterung ohne Visual Studio SDK  
  
1.  Erstellen Sie ein Windows-Verzeichnis, das die folgenden drei Dateien enthält:  
  
    -   *YourProfile* `.profile`  
  
    -   `extension.vsixmanifest`  
  
    -   `[Content_Types].xml` – Geben Sie diesen Namen wie hier gezeigt mit den eckigen Klammern ein.  
  
2.  Bearbeiten Sie `[Content_Types].xml` so, dass darin der folgende Text enthalten ist. Beachten Sie, dass ein Eintrag für jede Dateinamenerweiterung enthalten ist.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
      <Default Extension="profile" ContentType="application/octet-stream" />  
      <Default Extension="vsixmanifest" ContentType="text/xml" />  
    </Types>  
    ```  
  
3.  Kopieren Sie ein vorhandenes `extension.vsixmanifest`-Element, und bearbeiten Sie es mit einem XML-Editor. Ändern Sie die Knoten für ID, Name und Inhalt.  
  
    -   Sie finden ein Beispiel für `extension.vsixmanifest` in diesem Verzeichnis:  
  
         *Laufwerk* **: \Programme\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**  
  
    -   Der Knoten "Inhalt" sollte wie folgt aussehen:  
  
        ```  
        <Content>  
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"  
          >YourProfile.Profile</CustomExtension>  
        </Content>  
        ```  
  
4.  Komprimieren Sie die drei Dateien in einer ZIP-Datei.  
  
     Wählen Sie im Windows-Explorer die drei Dateien, mit der rechten Maustaste, zeigen Sie auf **senden an**, und klicken Sie dann auf **komprimierten (gezippten) Ordner**.  
  
5.  Benennen Sie die ZIP-Datei um, und ändern Sie die Dateierweiterung von `.zip` in `.vsix`.  
  
6.  Um das Profil auf einem Computer mit den geeigneten Editionen von Visual Studio zu installieren, doppelklicken Sie auf die `.vsix`-Datei.  
  
#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>So installieren Sie ein UML-Profil aus einer Visual Studio-Erweiterung  
  
1.  Doppelklicken Sie im Windows-Explorer auf die `.vsix`-Datei, oder öffnen Sie diese in Visual Studio.  
  
2.  Klicken Sie auf **installieren** im Dialogfeld, das angezeigt wird.  
  
3.  Öffnen Sie zum Deinstallieren oder vorübergehend deaktivieren Sie die Erweiterung, **Erweiterungen und Updates** aus der **Tools** Menü.  
  
##  <a name="Localized"></a> Definieren lokalisierter Profile  
 Sie können verschiedene Profile für andere Kulturen oder Sprachen definieren und alle in derselben Erweiterung verpacken. Wenn Benutzer die Erweiterung laden, sehen diese das Profil, das Sie für die jeweilige Kultur definiert haben.  
  
 Sie müssen immer ein Standardprofil bereitstellen. Wenn Sie kein Profil für die Kultur eines Benutzers definiert haben, wird das Standardprofil angezeigt.  
  
#### <a name="to-define-a-localized-profile"></a>So definieren Sie ein lokalisiertes Profil  
  
1.  Erstellen Sie ein Profil aus, in den vorherigen Abschnitten beschriebenen[Gewusst wie: Definieren eines Profils](#DefineProfile) und [Gewusst wie: Hinzufügen eines Profils zu einer Visual Studio-Erweiterung](#AddProfile). Dies ist das Standardprofil, das für alle Installationen verwendet wird, für die Sie kein lokalisiertes Profil bereitstellen.  
  
2.  Fügen Sie im Verzeichnis, in dem sich die Datei mit dem Standardprofil befindet, ein neues Verzeichnis hinzu.  
  
    > [!NOTE]
    >  Falls Sie die Erweiterung mithilfe eines Visual Studio-Erweiterungsprojekts erstellen, verwenden Sie den Projektmappen-Explorer, um dem Projekt einen neuen Ordner hinzuzufügen.  
  
3.  Ändern Sie den Namen des neuen Verzeichnisses in den ISO-Kurzcode für die lokalisierte Kultur, z. B. `bg` für Bulgarisch oder `fr` für Französisch. Sie sollten einen neutralen Kulturcode verwenden, also in der Regel zwei Buchstaben. Verwenden Sie keine speziellen Kulturcodes wie `fr-CA`. Weitere Informationen zu kulturcodes finden Sie unter [CultureInfo.GetCultures-Methode](http://go.microsoft.com/fwlink/?LinkId=160782), die eine vollständige Liste der kulturcodes bereitstellt.  
  
4.  Fügen Sie dem neuen Verzeichnis eine Kopie des Standardprofils hinzu. Ändern Sie den Dateinamen nicht.  
  
     Ein Beispiel für [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Erweiterungsordner, bevor sie Build oder eine in Komprimierung einer `.vsix` Datei, die folgenden Ordner und Dateien enthält:  
  
     `extension.vsixmanifest`  
  
     `MyProfile.profile`  
  
     `fr\MyProfile.profile`  
  
     `de\MyProfile.profile`  
  
    > [!NOTE]
    >  Sie sollten in `extension.vsixmanifest` keinen Verweis auf die lokalisierten Versionen der Profile einfügen. Die kopierten Profildateien müssen den gleichen Namen wie das Profil im übergeordneten Ordner haben.  
  
5.  Bearbeiten Sie die neue Kopie des Profils, indem Sie alle für Benutzer sichtbaren Elemente in die Zielsprache übersetzen, z. B. die `displayName`-Attribute.  
  
6.  Sie können zusätzliche Kulturordner und lokalisierte Profile für beliebig viele Kulturen erstellen.  
  
7.  Erstellen Sie die Visual Studio-Erweiterung, indem Sie entweder das Erweiterungsprojekt erstellen oder alle Dateien komprimieren, wie in den vorherigen Abschnitten beschrieben.  
  
##  <a name="Schema"></a> Die Struktur eines Profils  
 Die XSD-Datei für UML-Profile finden Sie im folgenden Beispiel: [Festlegen von Stereotypen und XSD-Profilen](http://go.microsoft.com/fwlink/?LinkID=213811). Installieren Sie die `.xsd`-Datei zur Unterstützung der Bearbeitung von Profildateien in:  
  
 **%ProgramFiles%\Microsoft visual Studio [Version] \Xml\Schemas**  
  
 Dieser Abschnitt verwendet als Beispiel das C#-Profil. Sie finden die vollständige Profildefinition unter:  
  
 *Laufwerk* **: \Programme\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile**  
  
 Die ersten Teile dieses Pfads können in Ihrer Installation ggf. abweichen.  
  
 Weitere Informationen zum .NET-Profil finden Sie unter [Standardstereotype für UML-Modelle](../modeling/standard-stereotypes-for-uml-models.md).  
  
### <a name="main-sections-of-the-uml-profile-definition"></a>Hauptabschnitte der UML-Profildefinition  
 Jedes Profil enthält den folgenden Inhalt:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<profile dslVersion="1.0.0.0"   
       name="CSharpProfile" displayName="C# Profile"   
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">  
  <stereotypes>...</stereotypes>  
  <metaclasses>...</metaclasses>  
  <propertyTypes>...</propertyTypes>  
</profile>  
```  
  
> [!NOTE]
>  Das Attribut `name` darf keine Leerzeichen oder Interpunktionszeichen enthalten. Das Attribut `displayName` wird auf der Benutzeroberfläche angezeigt und sollte eine gültige XML-Zeichenfolge sein.  
  
 Jedes Profil enthält drei Hauptabschnitte. Dies sind in umgekehrter Reihenfolge:  
  
-   `<propertyTypes>` – Eine Liste von Typen, die für Eigenschaften verwendet werden, die im Abschnitt mit den Stereotypen definiert sind.  
  
-   `<metaclasses>` – Eine Liste mit Modellelementtypen, für die die Stereotype in diesem Profil gelten, z. B. IClass, IInterface, IOperation, IDependency.  
  
-   `<stereotypes>` – Die Stereotypdefinitionen. Jede Definition enthält die Namen und die Typen von Eigenschaften, die dem Zielmodellelement hinzugefügt werden.  
  
#### <a name="property-types"></a>Eigenschaftentypen  
 Die `<propertyTypes>` -Abschnitt deklariert eine Liste von Typen, die verwendet werden, für Eigenschaften in der `<stereotypes>` Abschnitt. Es gibt zwei Arten von Eigenschaftentypen: extern und Enumeration.  
  
 Ein externer Typ deklariert den vollqualifizierten Namen eines .NET-Standardtyps:  
  
```  
<externalType name="System.String" />  
```  
  
 Ein Enumerationstyp definiert einen Satz von Literalwerten:  
  
```  
<enumerationType name="PackageVisibility">  
  <enumerationLiterals>  
    <enumerationLiteral name="internal" displayName="internal"  />  
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />  
  </enumerationLiterals>  
</enumerationType>  
```  
  
#### <a name="metaclasses"></a>Metaklassen  
 Der `<metaclasses>`-Abschnitt ist eine Liste von Modellelementtypen, für die Stereotype in diesem Profil definiert werden können:  
  
```  
<metaclass   
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />  
```  
  
 Die vollständige Liste der Modellelement- und Beziehungstypen Modelltypen, die Sie als Metaklassen verwenden können, finden Sie unter [Modellelementtypen](#Elements).  
  
#### <a name="stereotype-definition"></a>Stereotypdefinition  
 Der `<stereotypes>`-Abschnitt enthält eine oder mehrere Stereotypdefinitionen:  
  
```  
<stereotype name="CSharpClass" displayName="C# Class"> ...  
```  
  
 Jedes Stereotyp führt einen oder mehrere Modellelement- oder Beziehungstypen auf, auf die es angewendet werden kann. Sie können den Namen eines Basistyps angeben, um alle abgeleiteten Typen einzubeziehen. Wenn Sie z. B. `Microsoft.VisualStudio.Uml.Classes.IType` angeben, kann das Stereotyp auf `IClass`, `IInterface`, `IEnumeration` und verschiedene andere Typen von Elementen angewendet werden.  
  
```  
<metaclasses>  
  <metaclassMoniker name=  
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />  
</metaclasses>  
```  
  
 Das `name`-Attribut von `metaclassMoniker` ist ein Link zu einem Element im `<metaClasses>`-Abschnitt.  
  
> [!NOTE]
>  Der Monikername muss mit `/yourProfileName/` beginnen, wobei `yourProfileName` im `name`-Attribut des Profils definiert ist ("CSharpProfile" in diesem Beispiel). Der Moniker endet mit dem Namen von einem der Einträge im metaclasses-Abschnitt.  
  
 Jedes Stereotyp kann keine oder mehrere Eigenschaften aufführen, die es jedem Modellelement hinzufügt, auf das es angewendet wird. Die `<propertyType>` enthält einen Link zu einer der Typen, die definiert sind die `<propertyTypes>` Abschnitt. Der Link muss entweder `<externalTypeMoniker>` sein, um auf `<externalType>,` zu verweisen, oder `<enumerationTypeMoniker>`, um auf `<enumerationType>` zu verweisen. Der Link beginnt wieder mit dem Namen des Profils.  
  
```  
  <properties>  
    <property name="IsStatic"   
            displayName="Is Static" defaultValue="false">  
      <propertyType>  
<externalTypeMoniker   
               name="/CSharpProfile/System.Boolean" />  
      </propertyType>  
    </property>  
    <property name="PackageVisibility"   
              displayName="Package Visibility"  
              defaultValue="internal">  
      <propertyType>  
        <enumerationTypeMoniker   
              name="/CSharpProfile/PackageVisibility"/>  
      </propertyType>  
    </property>  
  </properties>  
</stereotype>  
```  
  
##  <a name="Elements"></a> Modellelementtypen  
 Der Satz von Typen, die für die Stereotype definiert werden können finden Sie [UML-Modellelementtypen](../modeling/uml-model-element-types.md).  
  
## <a name="troubleshooting"></a>Problembehandlung  
 Meine Stereotype werden nicht in den UML-Modellen angezeigt.  
 Das Profil muss als Paket oder Modell ausgewählt werden. Anschließend werden die Stereotype auf Elementen in dem Paket oder Modell angezeigt. Weitere Informationen finden Sie unter [Hinzufügen von Stereotypen zu UML-Modellelemente](../modeling/add-stereotypes-to-uml-model-elements.md).  
  
 Der folgende Fehler angezeigt wird, beim Öffnen eines UML-Modells: **VS1707: die folgenden Profile können nicht geladen werden, weil Fehler bei der Serialisierung: MyProfile.profile**  
 1.  Überprüfen Sie, ob die grundlegende XML-Syntax der PROFILE-Datei korrekt ist.  
  
2. Stellen Sie sicher, dass jeder Monikername das Format "/Profilname/Knotenname" besitzt. Der "Profilname" ist der Wert des name-Attributs im Stammprofilknoten. Der "Knotenname" ist der Wert des name-Attributs einer Metaklasse (metaclass), eines externen Typs (externalType) oder eines Enumerationstyps (enumerationType).  
  
3. Sicherstellen, dass die Syntax ist, wie hier beschrieben und wie in _Laufwerk_**: \Programme\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .  
  
4. Deinstallieren Sie die fehlerhafte Erweiterung. Klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**.  
  
   -   Wenn die Erweiterung nicht angezeigt wird, gehen Sie wie im Folgenden beschrieben vor.  
  
5. Erstellen Sie die VSIX-Datei neu, und öffnen Sie sie in Windows-Explorer, um sie erneut zu installieren. Starten Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]neu.  
  
   Die Erweiterung wird nicht im Erweiterungs-Manager angezeigt, aber wenn Sie versuchen, sie erneut zu installieren, wird die folgende Meldung angezeigt: **die Erweiterung bereits für alle entsprechenden Produkte installiert ist.**  
   1.  Entfernen Sie die Erweiterungsdatei aus einem Unterordner des *LocalAppData*\Microsoft\VisualStudio\\[Version] \Extensions\  
  
   -   Um finden Sie unter *LocalAppData*, müssen Sie versteckte Dateien und Ordner in der Registerkarte Ansicht der Optionen für die Windows-Explorer festlegen.  
  
   -   *LocalAppData* umfasst i. d. r. C:\Users\\*Benutzername*\AppData\Local\  
  
6. Starten Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]neu.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Stereotypen zu UML-Modellelementen](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Standardstereotype für UML-Modelle](../modeling/standard-stereotypes-for-uml-models.md)   
 [Beispiel: Color UML-Elementen nach Stereotyp](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Beispiel: Festlegen von Stereotypen, Profile XSD](http://go.microsoft.com/fwlink/?LinkID=213811)



