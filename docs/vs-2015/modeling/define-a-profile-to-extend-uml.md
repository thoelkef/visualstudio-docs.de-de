---
title: Definieren eines Profils zum Erweitern von UML | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b680c2e27b871e654618b4c0ada0904744751282
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850472"
---
# <a name="define-a-profile-to-extend-uml"></a>Definieren eines Profils zum Erweitern von UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein *UML-Profil* definieren, um die Standardmodell Elemente für bestimmte Zwecke anzupassen. Ein Profil definiert eine oder mehrere *UML-Stereotype*. Ein Stereotyp kann verwendet werden, um einen Typ als Darstellung einer bestimmten Art Objekt zu markieren. Ein Stereotyp kann außerdem verwendet werden, um die Liste der Eigenschaften eines Elements zu erweitern.

 Mehrere Profile werden mit unterstützten Editionen von Visual Studio installiert. Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Weitere Informationen zu diesen Profilen und zum Anwenden von Stereotypen finden Sie unter [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 Sie können eigene Profile definieren, um UML an Ihren eigenen Geschäftsbereich oder Ihre Architektur anzupassen und bei Bedarf zu erweitern. Beispiel:

- Wenn Sie häufig Websites definieren, können Sie ein eigenes Profil definieren, das ein Stereotyp "Webseite" bereitstellt, das in Klassendiagrammen auf Klassen angewendet werden kann. Sie können mithilfe von Klassendiagrammen dann eine Website planen. Jede "Webseite"-Klasse enthält zusätzliche Eigenschaften für Seiteninhalt, Format usw.

- Wenn Sie Banksoftware entwickeln, können Sie ein Profil definieren, das ein "Konto"-Stereotyp bereitstellt. Sie können dann Klassendiagramme verwenden, um andere Kontotypen zu definieren und die Beziehungen zwischen ihnen anzuzeigen.

  Sie können eigene Profile an das Team verteilen. Jedes Teammitglied kann das Profil installieren. Auf diese Weise können die Teammitglieder Modelle bearbeiten und erstellen, die die Stereotype verwenden.

> [!NOTE]
> Wenn Sie die Stereotype eines Profils in einem Modell anwenden, das Sie bearbeiten, und das Modell dann für andere Personen freigeben, sollten diese Personen auf ihren Computern das gleiche Profil installieren. Andernfalls sind sie nicht in der Lage, die Stereotype anzuzeigen, die Sie verwendet haben.

 Ein Profil ist häufig Teil einer größeren [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Erweiterung. Sie können z. B. einen Befehl definieren, der einige Teile eines Modells in Code übersetzt. Sie können ein Profil definieren, das Benutzer auf Pakete anwenden müssen, die sie übersetzen möchten. In diesem Fall verteilen Sie den neuen Befehl gemeinsam mit dem Profil in einer einzelnen [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Erweiterung.

 Sie können auch lokalisierte Varianten eines Profils definieren. Benutzer, die die Erweiterung laden, sehen die Variante, die für ihre eigene Kultur geeignet ist.

## <a name="DefineProfile"></a>Definieren eines Profils

#### <a name="to-define-a-uml-profile"></a>So definieren Sie ein UML-Profil

1. Erstellen Sie eine neue XML-Datei mit der Dateinamenerweiterung `.profile`.

2. Fügen Sie Stereotype-Definitionen gemäß den Richtlinien hinzu, die in [der Struktur eines Profils](#Schema)beschrieben werden.

3. Fügen Sie das Profil einer Visual Studio-Erweiterung hinzu (`.vsix`-Datei). Sie können entweder eine neue Erweiterung für das Profil erstellen oder dem Profil eine vorhandene Erweiterung hinzufügen.

     Weitere Informationen finden Sie im nächsten Abschnitt [Hinzufügen eines Profils zu einer Visual Studio-Erweiterung](#AddProfile).

4. Installieren Sie die Erweiterung auf dem Computer.

    1. Doppelklicken Sie auf die Erweiterungsdatei mit der Dateierweiterung `.vsix`.

    2. Starten Sie Visual Studio neu.

5. Überprüfen Sie, ob das Profil installiert wurde.

    1. Wählen Sie das Modell in UML-Explorer aus.

    2. Klicken Sie im Eigenschaftenfenster auf die Eigenschaft **profile** . Das Profil wird im Menü angezeigt. Setzen Sie das Häkchen neben dem Profil.

    3. Wählen Sie ein Element aus, für welches das Profil Stereotype definiert. Klicken Sie im Eigenschaftenfenster auf die Eigenschaft **Stereotype** . Die Stereotype werden in der Liste aufgeführt. Setzen bei einem der Stereotype ein Häkchen.

    4. Wenn das Profil zusätzliche Eigenschaften für dieses Stereotyp definiert, erweitern Sie die Stereotypeigenschaft, um sie anzuzeigen.

6. Senden Sie die Erweiterungsdatei an andere Benutzer von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], damit diese sie auf ihren Computern installieren können.

## <a name="AddProfile"></a>Hinzufügen eines Profils zu einer Visual Studio-Erweiterung
 Um ein Profil zu installieren und das Senden an andere Benutzer zu ermöglichen, müssen Sie das Profil einer Visual Studio-Erweiterung hinzufügen. Weitere Informationen finden Sie unter Bereitstellen von [Visual Studio-Erweiterungen](https://msdn.microsoft.com/library/dd393694(VS.100).aspx).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>So definieren Sie ein Profil in einer neuen Visual Studio-Erweiterung

1. Erstellen Sie ein Visual Studio-Erweiterungsprojekt.

   > [!NOTE]
   > Um dieses Verfahren durchführen zu können, muss [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] installiert sein.

   1. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

   2. Erweitern Sie im Dialogfeld **Neues Projekt** unter **installierte Vorlagen**die Option **Visualisierung C#** , klicken Sie auf **Erweiterbarkeit**, und klicken Sie dann auf **VSIX-Projekt**. Legen Sie Projektname fest, und klicken Sie auf **OK**.

2. Fügen Sie das Profil dem Projekt hinzu.

   - Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Vorhandenes Element**. Suchen Sie im Dialogfeld nach der Profildatei.

3. Legen Sie die Eigenschaft **in Ausgabe kopieren** der Profil Datei fest.

   1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Profil Datei, und klicken Sie dann auf **Eigenschaften**.

   2. Legen Sie im Eigenschaftenfenster die Eigenschaft in **Ausgabeverzeichnis kopieren** auf **immer kopieren**fest.

4. Öffnen Sie im Projektmappen-Explorer die Erweiterung `source.extension.vsixmanifest`.

    Die Datei wird im Erweiterungsmanifest-Editor geöffnet.

5. Fügen Sie auf der Seite **Assets** eine Zeile hinzu, in der das Profil beschrieben wird:

   - Klicken Sie auf **New** (Neu). Legen Sie die Felder im Dialogfeld **Neues Objekt hinzufügen** wie folgt fest.

   - Legen Sie **Typ** auf `Microsoft.VisualStudio.UmlProfile` fest.

        Dies ist keine der Dropdown-Auswahlmöglichkeiten. Geben Sie diesen Namen über die Tastatur ein.

   - Klicken Sie **auf Datei im Dateisystem** , und wählen Sie den Namen der Profil Datei aus, z. b. `MyProfile.profile`

6. Erstellen Sie das Projekt.

7. Drücken Sie F5, **um das Profil zu Debuggen**.

    Eine experimentelle Instanz von Visual Studio wird geöffnet. Öffnen Sie in dieser Instanz ein Modellierungsprojekt. Wählen Sie im UML-Explorer das Stammelement des Modells und im Eigenschaftenfenster das Profil aus. Wählen Sie dann Elemente innerhalb der Modell- und Satzstereotypen aus, die Sie dafür definiert haben.

8. **So extrahieren Sie die VSIX für die Bereitstellung**

   1. Öffnen Sie in Windows-Explorer den Ordner " **.\bin\debug** " oder " **.\bin\release** ", um die **VSIX** -Datei zu suchen. Dies ist eine [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Erweiterungsdatei. Sie kann auf dem Computer installiert und an andere Visual Studio-Benutzer gesendet werden.

   2. So installieren Sie die Erweiterung:

       1. Doppelklicken Sie auf die `.vsix`-Datei. Der Installer für Visual Studio-Erweiterungen wird gestartet.

       2. Starten Sie alle Instanzen von Visual Studio neu, die ausgeführt werden.

   Sie können das folgende alternative Verfahren für kleine Erweiterungen verwenden, falls Sie [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] nicht installiert haben.

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>So definieren Sie eine Profilerweiterung ohne Visual Studio SDK

1. Erstellen Sie ein Windows-Verzeichnis, das die folgenden drei Dateien enthält:

    - *YourProfile* `.profile`

    - `extension.vsixmanifest`

    - `[Content_Types].xml`-geben Sie diesen Namen ein, wie hier gezeigt, mit den eckigen Klammern.

2. Bearbeiten Sie `[Content_Types].xml` so, dass darin der folgende Text enthalten ist. Beachten Sie, dass ein Eintrag für jede Dateinamenerweiterung enthalten ist.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="profile" ContentType="application/octet-stream" />
      <Default Extension="vsixmanifest" ContentType="text/xml" />
    </Types>
    ```

3. Kopieren Sie ein vorhandenes `extension.vsixmanifest`-Element, und bearbeiten Sie es mit einem XML-Editor. Ändern Sie die Knoten für ID, Name und Inhalt.

    - Sie finden ein Beispiel für `extension.vsixmanifest` in diesem Verzeichnis:

         *Laufwerk* **: \Programme\Microsoft Visual Studio [Version] \common7\ide\extensions\microsoft\architecture tools\verlprofiles**

    - Der Knoten "Inhalt" sollte wie folgt aussehen:

        ```
        <Content>
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"
          >YourProfile.Profile</CustomExtension>
        </Content>
        ```

4. Komprimieren Sie die drei Dateien in einer ZIP-Datei.

     Wählen Sie in Windows-Explorer die drei Dateien aus, klicken Sie mit der rechten Maustaste auf, zeigen Sie auf **Senden an**, und klicken Sie dann auf **ZIP-komprimierter Ordner**.

5. Benennen Sie die ZIP-Datei um, und ändern Sie die Dateierweiterung von `.zip` in `.vsix`.

6. Um das Profil auf einem Computer mit den geeigneten Editionen von Visual Studio zu installieren, doppelklicken Sie auf die `.vsix`-Datei.

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>So installieren Sie ein UML-Profil aus einer Visual Studio-Erweiterung

1. Doppelklicken Sie im Windows-Explorer auf die `.vsix`-Datei, oder öffnen Sie diese in Visual Studio.

2. Klicken Sie im angezeigten Dialogfeld auf **Installieren** .

3. Um die Erweiterung zu deinstallieren oder vorübergehend zu deaktivieren, öffnen Sie im **Menü Extras die Option** **Erweiterungen und Updates** .

## <a name="Localized"></a>Definieren lokalisierter profile
 Sie können verschiedene Profile für andere Kulturen oder Sprachen definieren und alle in derselben Erweiterung verpacken. Wenn Benutzer die Erweiterung laden, sehen diese das Profil, das Sie für die jeweilige Kultur definiert haben.

 Sie müssen immer ein Standardprofil bereitstellen. Wenn Sie kein Profil für die Kultur eines Benutzers definiert haben, wird das Standardprofil angezeigt.

#### <a name="to-define-a-localized-profile"></a>So definieren Sie ein lokalisiertes Profil

1. Erstellen Sie wie in den vorherigen Abschnitten[Definieren eines Profils](#DefineProfile) und [Hinzufügen eines Profils zu einer Visual Studio-Erweiterung](#AddProfile)beschrieben ein Profil. Dies ist das Standardprofil, das für alle Installationen verwendet wird, für die Sie kein lokalisiertes Profil bereitstellen.

2. Fügen Sie im Verzeichnis, in dem sich die Datei mit dem Standardprofil befindet, ein neues Verzeichnis hinzu.

    > [!NOTE]
    > Falls Sie die Erweiterung mithilfe eines Visual Studio-Erweiterungsprojekts erstellen, verwenden Sie den Projektmappen-Explorer, um dem Projekt einen neuen Ordner hinzuzufügen.

3. Ändern Sie den Namen des neuen Verzeichnisses in den ISO-Kurzcode für die lokalisierte Kultur, z. B. `bg` für Bulgarisch oder `fr` für Französisch. Sie sollten einen neutralen Kulturcode verwenden, also in der Regel zwei Buchstaben. Verwenden Sie keine speziellen Kulturcodes wie `fr-CA`. Weitere Informationen zu Kultur Codes finden Sie unter [CultureInfo. GetCultures-Methode](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx), die eine komplette Liste der Kultur Codes enthält.

4. Fügen Sie dem neuen Verzeichnis eine Kopie des Standardprofils hinzu. Ändern Sie den Dateinamen nicht.

     Ein Beispiel [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Erweiterungs Ordners, bevor es in einer `.vsix` Datei erstellt oder komprimiert wird, würde die folgenden Ordner und Dateien enthalten:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > Sie sollten in `extension.vsixmanifest` keinen Verweis auf die lokalisierten Versionen der Profile einfügen. Die kopierten Profildateien müssen den gleichen Namen wie das Profil im übergeordneten Ordner haben.

5. Bearbeiten Sie die neue Kopie des Profils, indem Sie alle für Benutzer sichtbaren Elemente in die Zielsprache übersetzen, z. B. die `displayName`-Attribute.

6. Sie können zusätzliche Kulturordner und lokalisierte Profile für beliebig viele Kulturen erstellen.

7. Erstellen Sie die Visual Studio-Erweiterung, indem Sie entweder das Erweiterungsprojekt erstellen oder alle Dateien komprimieren, wie in den vorherigen Abschnitten beschrieben.

## <a name="Schema"></a>Struktur eines Profils
 Die XSD-Datei für UML-Profile finden Sie im folgenden Beispiel: [Festlegen von Stereotypen und Profilen XSD](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples). Installieren Sie die `.xsd`-Datei zur Unterstützung der Bearbeitung von Profildateien in:

 **%ProgramFiles%\Microsoft Visual Studio [Version] \Xml\Schemas**

 Dieser Abschnitt verwendet als Beispiel das C#-Profil. Sie finden die vollständige Profildefinition unter:

 *Laufwerk* **: \Programme\Microsoft Visual Studio [Version] \common7\ide\extensions\microsoft\architecture tools\verlprofiles\csharp.profile**

 Die ersten Teile dieses Pfads können in Ihrer Installation ggf. abweichen.

 Weitere Informationen zum .NET-Profil finden Sie unter [Standard Stereotype für UML-Modelle](../modeling/standard-stereotypes-for-uml-models.md).

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
> Das Attribut `name` darf keine Leerzeichen oder Interpunktionszeichen enthalten. Das Attribut `displayName` wird auf der Benutzeroberfläche angezeigt und sollte eine gültige XML-Zeichenfolge sein.

 Jedes Profil enthält drei Hauptabschnitte. Dies sind in umgekehrter Reihenfolge:

- `<propertyTypes>`: eine Liste der Typen, die für Eigenschaften verwendet werden, die im Abschnitt Stereotype definiert sind.

- `<metaclasses>` – Eine Liste mit Modellelementtypen, für die die Stereotype in diesem Profil gelten, z. B. IClass, IInterface, IOperation, IDependency.

- `<stereotypes>`: die stereotype-Definitionen. Jede Definition enthält die Namen und die Typen von Eigenschaften, die dem Zielmodellelement hinzugefügt werden.

#### <a name="property-types"></a>Eigenschaftstypen
 Der Abschnitt "`<propertyTypes>`" deklariert eine Liste der Typen, die im Abschnitt "`<stereotypes>`" für Eigenschaften verwendet werden. Es gibt zwei Arten von Eigenschaftentypen: extern und Enumeration.

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

 Die vollständige Liste der Modellelement-und Beziehungstypen, die Sie als Metaclasses verwenden können, finden Sie unter [Modellelement Typen](#Elements).

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
> Der Monikername muss mit `/yourProfileName/` beginnen, wobei `yourProfileName` im `name`-Attribut des Profils definiert ist ("CSharpProfile" in diesem Beispiel). Der Moniker endet mit dem Namen von einem der Einträge im metaclasses-Abschnitt.

 Jedes Stereotyp kann keine oder mehrere Eigenschaften aufführen, die es jedem Modellelement hinzufügt, auf das es angewendet wird. Der `<propertyType>` enthält einen Link zu einem der Typen, die im `<propertyTypes>` Abschnitt definiert sind. Der Link muss entweder `<externalTypeMoniker>` sein, um auf `<externalType>,` zu verweisen, oder `<enumerationTypeMoniker>`, um auf `<enumerationType>` zu verweisen. Der Link beginnt wieder mit dem Namen des Profils.

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

## <a name="Elements"></a>Modell Element Typen
 Der Satz von Typen, für die Sie Stereotype definieren können, ist in den [UML-Modellelement Typen](../modeling/uml-model-element-types.md)aufgeführt.

## <a name="troubleshooting"></a>Problembehandlung
 Meine Stereotype werden nicht in den UML-Modellen angezeigt.
Das Profil muss als Paket oder Modell ausgewählt werden. Anschließend werden die Stereotype auf Elementen in dem Paket oder Modell angezeigt. Weitere Informationen finden Sie unter [Hinzufügen von Stereotypen zu UML-Modellelementen](../modeling/add-stereotypes-to-uml-model-elements.md).

 Beim Öffnen eines UML-Modells wird der folgende Fehler angezeigt: **VS1707: die folgenden Profile können aufgrund eines serialisierungsfehlers nicht geladen werden: myProfile. profile**
1. Überprüfen Sie, ob die grundlegende XML-Syntax der PROFILE-Datei korrekt ist.

2. Stellen Sie sicher, dass jeder Monikername das Format "/Profilname/Knotenname" besitzt. Der "Profilname" ist der Wert des name-Attributs im Stammprofilknoten. Der "Knotenname" ist der Wert des name-Attributs einer Metaklasse (metaclass), eines externen Typs (externalType) oder eines Enumerationstyps (enumerationType).

3. Stellen Sie sicher, dass die Syntax wie hier beschrieben ist, und wie unter _Laufwerk_ **: \Programme\Microsoft Visual Studio [Version] \common7\ide\extensions\microsoft\architecture tools\umschlag\\** gezeigt.

4. Deinstallieren Sie die fehlerhafte Erweiterung. Klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**.

   - Wenn die Erweiterung nicht angezeigt wird, gehen Sie wie im Folgenden beschrieben vor.

5. Erstellen Sie die VSIX-Datei neu, und öffnen Sie sie in Windows-Explorer, um sie erneut zu installieren. Starten Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]neu.

   Die Erweiterung wird nicht im Erweiterungs-Manager angezeigt, aber wenn Sie versuchen, Sie erneut zu installieren, wird die folgende Meldung angezeigt: **die Extension ist bereits für alle anwendbaren Produkte installiert.**
   1. Entfernen Sie die Erweiterungs Datei aus einem Unterordner von *LocalAppData*\microsoft\visualstudio\\[Version] \extensions\

   - Um *LocalAppData*anzuzeigen, müssen Sie in den Ordneroptionen von Windows-Explorer auf der Registerkarte Ansicht die Option Ausgeblendete Dateien und Ordner anzeigen festlegen.

   - *LocalAppData* befindet sich normalerweise unter "c:\Users\\*username*\AppData\Local\".

6. Starten Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]neu.

## <a name="see-also"></a>Siehe auch
 [Hinzufügen von Stereotypen zu UML-Modellelementen](../modeling/add-stereotypes-to-uml-model-elements.md) [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Standard Stereotype für UML-Modelle](../modeling/standard-stereotypes-for-uml-models.md) [Beispiel: Color UML Elements by stereosample](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) [: Setting Stereotype, Profiles XSD](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)
