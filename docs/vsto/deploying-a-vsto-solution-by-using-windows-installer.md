---
title: Bereitstellen einer Visual Studio Tools for Office-Lösung mithilfe von Windows Installer
ms.date: 08/18/2010
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 876781cb6967f5d10dddccd54a46e218170445ab
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432198"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Bereitstellen einer Visual Studio Tools for Office-Lösung mithilfe von Windows Installer

## <a name="summary"></a>Zusammenfassung

Erfahren Sie, wie Sie ein Microsoft Visual Studio Tools for Office (VSTO)-Add-In oder eine Lösung auf Dokumentebene mithilfe eines Visual Studio Installer-Projekts bereitstellen.

Wouter van Vugt, Code Counsel

Ted Pattison, Ted Pattison Group

Dieser Artikel wurde von Microsoft mit DerGenehmigung der ursprünglichen Autoren aktualisiert.

**Gilt für:** Visual Studio Tools für Office, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Übersicht

Sie können eine VSTO-Lösung entwickeln und die Lösung mithilfe eines Windows Installer-Pakets bereitstellen. Diese Diskussion enthält Schritte zum Bereitstellen eines einfachen Office-Add-Ins.

## <a name="deployment-methods"></a>Bereitstellungsmethoden

ClickOnce kann einfach verwendet werden, um Setups für Ihre Add-Ins und Lösungen zu erstellen. Es können jedoch keine Add-Ins installiert werden, die Administratorrechte erfordern, z. B. Add-Ins auf Computerebene.

Add-Ins, die Administratorrechte erfordern, können mit Windows Installer installiert werden, es erfordert jedoch mehr Aufwand, um das Setup zu erstellen.

Eine Übersicht über die Bereitstellung einer VSTO-Lösung mithilfe von ClickOnce finden Sie [unter Bereitstellen einer Office-Lösung mithilfe von ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Bereitstellen von Office-Lösungen, die auf die VSTO-Laufzeit abzielen

ClickOnce- und Windows Installer-Pakete müssen bei der Installation einer Office-Lösung dieselben rudimentären Aufgaben ausführen.

1. Installieren Sie die erforderlichen Komponenten auf dem Benutzercomputer.
2. Stellen Sie die spezifischen Komponenten für die Lösung bereit.
3. Erstellen Sie für Add-Ins Registrierungseinträge.
4. Vertrauen Sie der Lösung, damit sie ausgeführt werden kann.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Erforderliche erforderliche Komponenten auf dem Zielcomputer

Hier ist die Liste der Software, die auf dem Computer installiert werden muss, um VSTO-Lösungen auszuführen:

- Microsoft Office 2010 oder neuer.
- Microsoft .NET Framework 4 oder neuer.
- Microsoft Visual Studio 2010-Tools für Office-Laufzeit.
  Die Laufzeit bietet eine Umgebung, in der Add-Ins und Lösungen auf Dokumentebene verwaltet werden. Eine Version der Runtime wird zwar mit Microsoft Office ausgeliefert, Aber Sie können eine bestimmte Version mit Ihrem Add-In weiterverteilen.
- Die primären Interopassemblys für Microsoft Office, wenn Sie keine eingebetteten Interop-Typen verwenden.
- Alle Dienstprogrammassemblys, auf die von Projekten verwiesen wird.

### <a name="specific-components-for-the-solution"></a>Spezifische Komponenten für die Lösung

Das Installationspaket muss diese Komponenten auf dem Computer des Benutzers installieren:

- Wenn Sie eine Lösung auf Dokumentebene erstellen, wenn Sie eine Lösung auf Dokumentebene erstellen.
- Die Anpassungsassembly und alle assemblys, die sie benötigt.
- Zusätzliche Komponenten, z. B. Konfigurationsdateien.
- Das Anwendungsmanifest (.manifest).
- Das Bereitstellungsmanifest (.vsto).

### <a name="registry-entries-for-add-ins"></a>Registrierungseinträge für Add-Ins

Microsoft Office verwendet Registrierungseinträge, um Add-Ins zu suchen und zu laden. Diese Registrierungseinträge sollten als Teil des Bereitstellungsprozesses erstellt werden. Weitere Informationen zu diesen Registrierungseinträgen finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](registry-entries-for-vsto-add-ins.md).

Outlook-Add-Ins, die benutzerdefinierte Formularbereiche anzeigen, erfordern zusätzliche Registrierungseinträge, mit denen die Formularbereiche identifiziert werden können. Weitere Informationen zu Registrierungseinträgen finden Sie unter [Registrierungseinträge für Outlook-Formularbereiche](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Lösungen auf Dokumentebene erfordern keine Registrierungseinträge. Stattdessen werden Eigenschaften innerhalb des Dokuments verwendet, um die Anpassung zu suchen. Weitere Informationen zu diesen Eigenschaften finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Vertrauen in die VSTO-Lösung

Damit eine Anpassung ausgeführt werden kann, muss der Computer einer Lösung vertrauen. Das Add-In kann vertrauenswürdig sein, indem sie das Manifest mit einem Zertifikat signiert, eine Vertrauensstellung mit einer Einschlussliste erstellt oder an einem vertrauenswürdigen Speicherort auf dem Computer installiert wird.

Weitere Informationen zum Abrufen eines Zertifikats zum Signieren finden Sie unter [ClickOnce-Bereitstellung und Authenticode](../deployment/clickonce-and-authenticode.md). Weitere Informationen zu vertrauenswürdigen Lösungen finden Sie unter [Vertrauen in Office-Lösungen mithilfe von Einschlusslisten](trusting-office-solutions-by-using-inclusion-lists.md). Sie können einen Eintrag in der Einschlussliste mit einer benutzerdefinierten Aktion in Ihrer Windows Installer-Datei hinzufügen. Weitere Informationen zum Aktivieren der Einschlussliste finden Sie unter [Gewusst wie: Konfigurieren der Inklusionslistensicherheit](how-to-configure-inclusion-list-security.md).

Wenn keine der beiden Optionen verwendet wird, wird dem Benutzer eine Vertrauensaufforderung angezeigt, damit er entscheiden kann, ob er der Lösung vertrauen soll.

Weitere Informationen zur Sicherheit im Zusammenhang mit Lösungen auf Dokumentebene finden Sie unter [Gewähren von Vertrauensstellungen für Dokumente](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Erstellen eines Basisinstallationsprogramms

Die Projektvorlagen Für Setup und Bereitstellung sind in der [Erweiterung Microsoft Visual Studio Installer Projects](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) enthalten, die zum Download zur Verfügung steht.

Um ein Installationsprogramm für eine Office-Lösung zu erstellen, müssen die folgenden Aufgaben ausgeführt werden:

- Fügen Sie die Komponenten der Office-Lösung hinzu, die bereitgestellt werden.
- Konfigurieren Sie für Add-Ins auf Anwendungsebene Registrierungsschlüssel.
- Konfigurieren Sie die erforderlichen Komponenten, damit sie auf den Endbenutzercomputern installiert werden können.
- Konfigurieren Sie Startbedingungen, um sicherzustellen, dass die erforderlichen erforderlichen Komponenten verfügbar sind. Startbedingungen können verwendet werden, um die Installation zu blockieren, wenn nicht alle erforderlichen Voraussetzungen installiert sind.

Der erste Schritt besteht darin, das Setupprojekt zu erstellen.

### <a name="to-create-the-addin-setup-project"></a>So erstellen Sie das AddIn-Setup-Projekt

1. Öffnen Sie das Office AddIn-Projekt, das Sie bereitstellen möchten. In diesem Beispiel verwenden wir ein Excel-Add-In namens ExcelAddIn.
2. Erweitern Sie mit Office Project Open im Menü **Datei** hinzufügen, **und** klicken Sie auf Neues **Projekt,** um ein neues Projekt hinzuzufügen.
::: moniker range="=vs-2017"
3. Erweitern Sie im Dialogfeld **Neues Projekt hinzufügen** andere **Projekttypen** im Bereich **Projekttypen,** erweitern Sie dann **Setup und Bereitstellung,** und wählen Sie dann **Visual Studio Installer aus.**
4. Wählen Sie im Bereich **Vorlagen** aus der Gruppe **"Installierte Vorlagen visual Studio"** die Option **Projekt** einrichten aus.
::: moniker-end
::: moniker range="=vs-2019"
3. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** die Vorlage **"Projekt einrichten"** aus.
4. Klicken Sie auf **Weiter**.
::: moniker-end

5. Geben Sie im Feld **Name** **OfficeAddInSetup**ein.
::: moniker range="=vs-2017"
6. Klicken Sie auf **Öffnen,** um das neue Setupprojekt zu erstellen.
::: moniker-end
::: moniker range="=vs-2019"
6. Klicken Sie auf **Erstellen,** um das neue Einrichtungsprojekt zu erstellen.
::: moniker-end

Visual Studio öffnet den Dateisystem-Explorer für das neue Setupprojekt. Mit dem Dateisystem-Explorer können Sie dateien zum Setupprojekt hinzufügen.

   ![Screenshot des Dateisystem-Explorers für das Setup-Projekt](media/setup-project-figure-1.png)

   **Abbildung 1: Dateisystem-Explorer für das Setup-Projekt**

Das Setupprojekt muss ExcelAddIn bereitstellen. Sie können das Setupprojekt für diesen Vorgang konfigurieren, indem Sie dem Setupprojekt die ExcelAddIn-Projektausgabe hinzufügen.

### <a name="to-add-the-exceladdin-project-output"></a>So fügen Sie die ExcelAddIn-Projektausgabe hinzu

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **OfficeAddInSetup**, klicken Sie auf **Hinzufügen** und dann **auf Projektausgabe**.
2. Wählen Sie im Dialogfeld **Projektausgabegruppe** hinzufügen das **ExcelAddIn** aus der Projektliste und die **primäre Ausgabe aus.**
3. Klicken Sie auf **OK,** um die Projektausgabe zum Setupprojekt hinzuzufügen.

    ![Screenshot des Dialogfelds Projekt projektausgabegruppe hinzufügen](media/setup-project-figure-2.png)

    **Abbildung 2: Setup-Projekt Projektausgabegruppen-Dialog hinzufügen**

Das Setupprojekt muss das Bereitstellungsmanifest und das Anwendungsmanifest bereitstellen. Fügen Sie diese beiden Dateien dem Setupprojekt als eigenständige Dateien aus dem Ausgabeordner des ExcelAddIn-Projekts hinzu.

### <a name="to-add-the-deployment-and-application-manifests"></a>So fügen Sie die Bereitstellungs- und Anwendungsmanifeste hinzu

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **OfficeAddInSetup**, klicken Sie auf **Hinzufügen**, und klicken Sie auf **Datei**.
2. Navigieren Sie im Dialogfeld **Dateien hinzufügen** zum **ExcelAddIn-Ausgabeverzeichnis.** In der Regel ist das Ausgabeverzeichnis der **\\Bin-Release-Unterordner** des Projektstammverzeichnisses, abhängig von der ausgewählten Buildkonfiguration.
3. Wählen Sie die Dateien **ExcelAddIn.vsto** und **ExcelAddIn.dll.manifest** aus, und klicken Sie auf **Öffnen,** um diese beiden Dateien zum Setupprojekt hinzuzufügen.

    ![Screenshot der Anwendungs- und Bereitstellungsmanifeste im Projektmappen-Explorer](media/setup-project-figure-3.jpg)

    **Abbildung 3: Anwendungs- und Bereitstellungsmanifeste für das Add-In im Projektmappen-Explorer**

Der Verweis auf ExcelAddIn enthält alle Komponenten, die ExcelAddIn benötigt. Diese Komponenten müssen ausgeschlossen und mithilfe von erforderlichen Paketen bereitgestellt werden, damit sie korrekt registriert werden können. Außerdem müssen die Softwarelizenzbedingungen angezeigt und akzeptiert werden, bevor die Installation beginnt.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>So schließen Sie die ExcelAddIn-Projektabhängigkeiten aus

1. Wählen Sie im **Projektmappen-Explorer**im **OfficeAddInSetup-Knoten** alle Abhängigkeitselemente unter dem Element **Erkannte Abhängigkeiten** mit Ausnahme von **Microsoft .NET Framework** oder einer Assembly aus, die mit ** \*endet. Utilities.dll**. Die Utilities-Assemblys sollen zusammen mit Ihrer Anwendung bereitgestellt werden.
2. Klicken Sie mit der rechten Maustaste auf die Gruppe, und wählen Sie **Eigenschaften**aus.
3. Ändern Sie im Fenster **Eigenschaften** die **Exclude-Eigenschaft** in **True,** um die abhängigen Assemblys aus dem Setupprojekt auszuschließen. Stellen Sie sicher, dass keine Utilities-Assemblys ausgeschlossen werden.

    ![Screenshot des Projektmappen-Explorers mit den auszuschließenden Abhängigkeiten](media/setup-project-figure-4.jpg)

    **Abbildung 4: Ausschließen von Abhängigkeiten**

Sie können Ihr Windows Installer-Paket so konfigurieren, dass erforderliche Komponenten installiert werden, indem Sie ein Setupprogramm hinzufügen, das auch als Bootstrapper bezeichnet wird. Dieses Setupprogramm kann die erforderlichen Komponenten installieren, ein Prozess namens Bootstrapping.

Für **ExcelAddIn**müssen diese Voraussetzungen installiert werden, bevor das Add-In ordnungsgemäß ausgeführt werden kann:

- Die Microsoft .NET Framework-Version, auf die die Office-Lösung abzielt.
- Microsoft Visual Studio 2010 Tools für Office-Laufzeit.

So konfigurieren Sie abhängige Komponenten als Voraussetzungen

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das **OfficeAddInSetup-Projekt,** und wählen Sie **Eigenschaften**aus.
2. Das Dialogfeld **OfficeAddInSetup-Eigenschaftenseiten** wird angezeigt.
3. Klicken Sie auf die Schaltfläche **Voraussetzungen.**
4. Wählen Sie im Dialogfeld Voraussetzungen die richtige Version von .NET Framework und Microsoft Visual Studio Tools for Office Runtime aus.

    ![Screenshot des Dialogfelds "Voraussetzungen"](media/setup-project-figure-5.png)

    **Abbildung 5: Dialogfeld "Voraussetzungen"**

    > [!NOTE]
    >Einige der konfigurierten Voraussetzungspakete in Ihrem Visual Studio-Setupprojekt sind von der ausgewählten Buildkonfiguration abhängig. Sie müssen für jede von Ihnen verwendete Buildkonfiguration die richtigen erforderlichen Komponenten auswählen.

Microsoft Office sucht Add-Ins mithilfe von Registrierungsschlüsseln. Die Schlüssel in\_der\_HKEY CURRENT USER-Struktur werden verwendet, um das Add-In für jeden einzelnen Benutzer zu registrieren. Die Schlüssel unter\_der\_HKEY LOCAL MACHINE-Struktur werden verwendet, um das Add-In für alle Benutzer des Computers zu registrieren. Weitere Informationen zu Registrierungsschlüsseln finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Konfigurieren der Registrierung

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **OfficeAddInSetup**.
2. Erweitern Sie **die Ansicht**.
3. Klicken Sie auf **Registrierung,** um das Registrierungseditorfenster zu öffnen.
4. Erweitern Sie im **Registry(OfficeAddInSetup)-Editor** **HKEY\_LOCAL\_MACHINE** und dann **Software**.
5. Löschen ** \[Sie\]** den Hersteller ?Key unter **HKEY\_LOCAL\_MACHINE\\Software**gefunden .
6. Erweitern Sie **HKEY\_\_CURRENT USER** und dann **Software**.
7. Löschen Sie den ** \[\] Herstellerschlüssel** unter **HKEY\_CURRENT\_USER\\Software**.
8. Um Registrierungsschlüssel für die Add-In-Installation hinzuzufügen, klicken Sie mit der rechten Maustaste auf den **Benutzer/Computer-Hive-Schlüssel,** wählen Sie **Neuer Schlüssel**. Verwenden Sie den Text **Software** für den Namen des neuen Schlüssels. Klicken Sie mit der rechten Maustaste auf den neu erstellten **Softwareschlüssel,** und erstellen Sie einen neuen Schlüssel mit dem Text **Microsoft**.
9. Verwenden Sie einen ähnlichen Prozess, um die gesamte Schlüsselhierarchie zu erstellen, die für die Add-In-Registrierung erforderlich ist:

    **Benutzer/Maschine\\Hive\\\\Software\\\\Microsoft Office\\Excel Addins SampleCompany.ExcelAddIn**

    Der Firmenname wird häufig als Präfix für den Namen des Add-Ins verwendet, um Eindeutigkeit bereitzustellen.

10. Klicken Sie mit der rechten Maustaste auf den **SampleCompany.ExcelAddIn-Schlüssel,** wählen Sie **Neu**aus, und klicken Sie auf **String-Wert**. Verwenden Sie den Text **Beschreibung** für den Namen.
11. Verwenden Sie diesen Schritt, um drei weitere Werte hinzuzufügen:
    - **FriendlyName** vom Typ **String**
    - **LoadBehavior** vom Typ **DWORD**
    - **Manifest** vom Typ **String**

12. Klicken Sie im Registrierungseditor mit der rechten Maustaste auf den **Wert Beschreibung,** und klicken Sie auf **Eigenschaftenfenster**. Geben Sie im **Eigenschaftenfenster** **Excel Demo AddIn** für die Value-Eigenschaft ein.
13. Wählen Sie den **FriendlyName-Schlüssel** im Registrierungseditor aus. Ändern Sie im **Eigenschaftenfenster**die **Value-Eigenschaft** in **Excel Demo AddIn**.
14. Wählen Sie den **LoadBehavior-Schlüssel** im Registrierungseditor aus. Ändern Sie im **Eigenschaftenfenster**die **Value-Eigenschaft** in **3.** Der Wert 3 für LoadBehavior gibt an, dass das Add-In beim Start der Hostanwendung geladen werden soll. Weitere Informationen zum Ladeverhalten finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](registry-entries-for-vsto-add-ins.md).

15. Wählen Sie den **Manifestschlüssel** im Registrierungseditor aus. Ändern Sie im **Eigenschaftenfenster**die **Value-Eigenschaft** in **file:///[TARGETDIR]ExcelAddIn.vsto|vstolocal**

    ![Screenshot des Registrierungs-Editors](media/setup-project-figure-6.png)

    **Abbildung 6: Einrichten von Registrierungsschlüsseln**

      Die VSTO-Laufzeit verwendet diesen Registrierungsschlüssel, um das Bereitstellungsmanifest zu finden. Das [TARGETDIR]-Makro wird durch den Ordner ersetzt, in dem das Add-In installiert ist. Das Makro enthält das nachfolgende Zeichen , daher sollte der Dateiname des Bereitstellungsmanifests ExcelAddIn.vsto ohne das Zeichen .
      Das **vstolocal-Postfix** teilt der VSTO-Laufzeit mit, dass das Add-In von diesem Speicherort anstelle des ClickOnce-Cache geladen werden soll. Wenn Sie dieses Postfix entfernen, wird die Anpassung von der Laufzeit in den ClickOnce-Cache kopiert.

   >[!WARNING]
   >Sie sollten mit dem Registrierungs-Editor in Visual Studio sehr vorsichtig sein. Wenn Sie beispielsweise versehentlich DeleteAtUninstall für den falschen Schlüssel festlegen, können Sie einen aktiven Teil der Registrierung löschen, sodass sich der Benutzercomputer in einem inkonsistenten oder sogar noch schlechteren Zustand befindet.

64-Bit-Versionen von Office verwenden die 64-Bit-Registrierungsstruktur, um nach Add-Ins zu suchen. Um Add-Ins unter der 64-Bit-Registrierungsstruktur zu registrieren, muss die Zielplattform des Setupprojekts nur auf 64 Bit festgelegt werden.

1. Wählen Sie das **OfficeAddInSetup-Projekt** im Projektmappen-Explorer aus.
2. Wechseln Sie zum **Eigenschaftenfenster,** und legen Sie die **TargetPlatform-Eigenschaft** auf **x64**fest.

Wenn Sie ein Add-In für 32-Bit- und 64-Bit-Versionen von Office installieren, müssen Sie zwei separate MSI-Pakete erstellen. Eine für 32-Bit und eine für 64-Bit.

  ![Screenshot des Eigenschaftenfensters mit der Zielplattform zum Registrieren von Add-Ins mit 64-Bit Office](media/setup-project-figure-7.jpg)

  **Abbildung 7: Zielplattform für die Registrierung von Add-Ins mit 64-Bit Office**

Wenn das MSI-Paket zum Installieren des Add-Ins oder der Lösung verwendet wird, kann es installiert werden, ohne dass die erforderlichen Voraussetzungen erforderlich sind. Sie können Die Startbedingungen in der MSI verwenden, um die Installation des Add-Ins zu blockieren, wenn die Voraussetzungen nicht installiert sind.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Konfigurieren einer Startbedingung zum Erkennen der VSTO-Runtime

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **OfficeAddInSetup**.
2. Erweitern Sie **die Ansicht**.
3. Klicken Sie auf **Startbedingungen**.
4. Klicken Sie im **Editor "Startbedingungen" (OfficeAddInSetup)** mit der rechten Maustaste auf **Anforderungen auf Zielcomputer**, und klicken Sie dann auf **Registrierungsstartbedingung hinzufügen**. Diese Suchbedingung kann in der Registrierung nach einem Schlüssel suchen, den die VSTO-Laufzeit installiert. Der Wert des Schlüssels ist dann für die verschiedenen Teile des Installers über eine benannte Eigenschaft verfügbar. Die Startbedingung verwendet die durch die Suchbedingung definierte Eigenschaft, um nach einem bestimmten Wert zu suchen.
5. Wählen Sie im Editor **"Startbedingungen" (OfficeAddInSetup)** die Suchbedingung **Suchen nach RegistryEntry1** aus, klicken Sie mit der rechten Maustaste auf die Bedingung, und wählen Sie **Eigenschaftenfenster**aus.

6. Legen Sie im **Eigenschaftsfenster** diese Eigenschaften fest:
   1. Legen Sie den Wert **von (Name)** auf **Suchen nach VSTO 2010 Runtime fest.**
   2. Ändern Sie den Wert der **Eigenschaft** in **VSTORUNTIMEREDIST**.
   3. Festlegen des Werts von **RegKey** auf **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4R**
   4. Lassen Sie die **Root-Eigenschaft** auf **vsdrrHKLM**festgelegt.
   5. Ändern Sie die **Value-Eigenschaft** in **Version**.

7. Wählen Sie im **Startbedingungen-Editor (OfficeAddInSetup)** die **Startbedingung Condition1** aus, klicken Sie mit der rechten Maustaste auf die Bedingung, und wählen Sie **Eigenschaftenfenster**aus.
8. Legen Sie im Eigenschaftsfenster diese Eigenschaften fest:
   1. Legen Sie den **(Name)** auf Überprüfen der **VERFÜGBARKEIT von VSTO 2010 Runtime**fest.
   2. Ändern des Wertes der **Bedingung** in **\>VSTORUNTIMEREDIST ="10.0.30319"**
   3. Lassen Sie die **InstallURL-Eigenschaft** leer.
   4. Festlegen der **Nachricht** auf **Visual Studio 2010 Tools for Office Runtime ist nicht installiert. Führen Sie Setup.exe aus, um das Add-In zu installieren.**

        ![Screenshot des Eigenschaftenfensters für die Startbedingung "Laufzeitverfügbarkeit überprüfen"](media/setup-project-figure-8.jpg)

        **Abbildung 8: Eigenschaftenfenster für die Startbedingung "Laufzeitverfügbarkeit überprüfen"**

 Die obige Startbedingung überprüft explizit, ob die VSTO-Laufzeit angezeigt wird, wenn sie vom Bootstrapperpaket installiert wird.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Konfigurieren einer Startbedingung zum Erkennen der von Office installierten VSTO-Runtime

1. Klicken Sie im **Editor "Startbedingungen" (OfficeAddInSetup)** mit der rechten Maustaste auf **Zielcomputer**suchen , und klicken Sie dann auf **Registrierungssuche hinzufügen**.
2. Wählen Sie die Suchbedingung **Suchen nach RegistryEntry1** aus, klicken Sie mit der rechten Maustaste auf die Bedingung, und wählen Sie **Eigenschaftenfenster**aus.
3. Legen Sie im **Eigenschaftsfenster** diese Eigenschaften fest:
    1. Legen Sie den Wert von **(Name)** auf **Suchen nach Office VSTO Runtime fest.**
    2. Ändern Sie den Wert der **Eigenschaft** in **OfficeRuntime**.
    3. Legen Sie den Wert von **RegKey** auf **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4**fest.
    4. Lassen Sie die **Root-Eigenschaft** auf **vsdrrHKLM**festgelegt.
    5. Ändern Sie die **Value-Eigenschaft** in **Version**.

4. Wählen Sie im **Startbedingungen-Editor (OfficeAddInSetup)** die zuvor definierte Verfügbarkeitsbedingung FÜR die **VSTO 2010-Laufzeit** überprüfung aus, klicken Sie mit der rechten Maustaste auf die Bedingung, und wählen Sie **Eigenschaftenfenster**aus.

5. Ändern Sie den Wert der **Condition-Eigenschaft** in **VSTORUNTIMEREDIST \>="10.0.30319" ODER OFFICERUNTIME\>="10.0.21022"**. Die Versionsnummern können für Sie unterschiedlich sein, abhängig von den Versionen der Laufzeit, die Ihr Add-In erfordert.

    ![Screenshot der Eigenschaften Windows für die Startbedingung](media/setup-project-figure-9.jpg)
  
    **Abbildung 9: Eigenschaften Von Windows für die Überprüfung der Laufzeitverfügbarkeit durch Redist oder Office-Startbedingung**

Wenn ein Add-In auf .NET Framework 4 oder neuer abzielt, können die Typen innerhalb der primären Interop-Assemblys (PIA), auf die verwiesen wird, in die VSTO-Assembly eingebettet werden.

So überprüfen Sie, ob die Interop-Typen in Ihr Add-In eingebettet werden, indem Sie die folgenden Schritte ausführen:

1. Erweitern des Referenzknotens im Projektmappen-Explorer
2. Wählen Sie einen der PIA-Referenzen aus, z. B. **Office**.
3. Zeigen Sie die Eigenschaftenfenster an, indem Sie F4 drücken oder Eigenschaften im Kontextmenü Assemblyauswählen auswählen.
4. Überprüfen Sie den Wert der Eigenschaft **Interop-Typen einbetten**.

Wenn der Wert auf **True**festgelegt ist, werden die Typen eingebettet, und Sie können zum Abschnitt [**So erstellen des Setupprojekts**](#to-build-the-setup-project) springen.

Weitere Informationen finden Sie unter [Typäquivalenz und Eingebettete Interop-Typen](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>So konfigurieren Sie Startbedingungen, um dies für Office-PIAs zu erkennen

1. Klicken Sie im **Editor "Startbedingungen" (OfficeAddInSetup)** mit der rechten Maustaste auf **Anforderungen auf Zielcomputer**, und klicken Sie dann auf Windows Installer Launch **Condition**hinzufügen . Diese Startbedingung sucht nach einer Office-PIA, indem nach der spezifischen Komponenten-ID gesucht wird.
2. Klicken Sie mit der rechten Maustaste auf **Suchen nach Komponente1,** und klicken Sie auf **Eigenschaftenfenster,** um die Eigenschaften der Startbedingung anzuzeigen.
3. Legen Sie im **Eigenschaftenfenster**die folgenden Eigenschaften fest:

    1. Ändern des Werts der **Eigenschaft (Name)** in **Suche nach freigegebener Office-PIA**
    2. Ändern Sie den Wert der **ComponentID** in Komponenten-ID für die office-Komponente, die Sie verwenden. Die Liste der Komponenten-IDs finden Sie in der folgenden Tabelle, z.B. in der Tabelle . . . . . **. . . . . . . . . . . . . . . . . .**. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    3. Ändern Sie den Wert der **Property-Eigenschaft** in **HASSHAREDPIA**.

4. Klicken Sie im **Editor "Startbedingungen" (OfficeAddInSetup)** mit der rechten Maustaste auf **Condition1,** und klicken Sie auf **Eigenschaftenfenster,** um die Eigenschaften der Startbedingung anzuzeigen.

5. Ändern Sie diese Eigenschaften von **Condition1**:

    1. Ändern Sie den **(Name)** in Überprüfen der **Verfügbarkeit von Office Shared PIA**.
    2. Ändern Sie die **Bedingung** in **HASSHAREDPIA**.
    3. Lassen Sie **InstallUrl** leer.
    4. Ändern der **Nachricht** in eine erforderliche Komponente für die **Interaktion mit Excel ist nicht verfügbar. Führen Sie setup.exe aus.**

    ![Screenshot des Eigenschaftenfensters für die Startbedingung "Verify Office Shared PIA"](media/setup-project-figure-10.jpg)
  
    **Abbildung 10: Eigenschaftenfenster für die Startbedingung "Verify Office Shared PIA"**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Komponenten-IDs der primären Interopassemblys für Microsoft Office

|Primäre Interop-Baugruppe|Office 2010|Office 2013|Office 2013 (64-Bit)|Office 2016|Office 2016 (64-Bit)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|EA7564AC-C67D-4868-BE5C-26E4FC2223FF|C8A65ABE-3270-4FD7-B854-50C8082C8F39|E3BD1151-B9CA-4D45-A77E-51A6E0ED322A|C4ACE6DB-AA99-401F-8BE6-8784BD09F003|C4ACE6DB-AA99-401F-8BE6-8784BD09F003|
|InfoPath|Nr. 4153F732-D670-4E44-8AB7-500F2B576BDA|Nr. 0F825A16-25B2-4771-A497-FC8AF3B355D8|C5BBD36E-B320-47EF-A512-556B9CB7E41|-|-|
|Outlook|Nr. 1D844339-3DAE-413E-BC13-62D6A52816B2|F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136|Nr. 7824A03F-28CC-4371-BC54-93D15EFC1E7F|7C6D92EF-7B45-46E5-8670-819663220E4E|7C6D92EF-7B45-46E5-8670-819663220E4E|
|PowerPoint|EECBA6B8-3A62-44AD-99EB-8666265466F9|Nr. 813139AD-6DAB-4DDD-8C6D-0CA30D073B41|05758318-BCFD-4288-AD8D-81185841C235|E0A76492-0FD5-4EC2-8570-AE1BAA61DC88|E0A76492-0FD5-4EC2-8570-AE1BAA61DC88|
|Visio|3EA123B5-6316-452E-9D51-A489E06E2347|C1713368-12A8-41F1-ACA1-934B01AD6EEB|Nr. 2CC0B221-22D2-4C15-A9FB-DE818E51AF75|2D4540EC-2C88-4C28-AE88-2614B5460648|2D4540EC-2C88-4C28-AE88-2614B5460648|
|Wort|Nr. 8B74A499-37F8-4DEA-B5A0-D72FC501CEFA|Nr. 9FE736B7-B1EE-410C-8D07-082891C3DAC8|Nr. 13C07AF5-B206-4A48-BB5B-B8022333E3CA|DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161|DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161|
|Microsoft Forms 2.0|B2279272-3FD2-434D-B94E-E4E0F8561AC4|B2279272-3FD2-434D-B94E-E4E0F8561AC4|A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC|-|-|
|Microsoft Graph|Nr. 011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E|Nr. 52DA4B37-B8EB-4B7F-89C1-824654CE4C70|Nr. 24706F33-F0CE-4EB4-BC91-9E935394F510|-|-|
|Smart Tag|Nr. 7102C98C-EF47-4F04-A227-FE33650BF954|Nr. 487A7921-EB3A-4262-BB5B-A5736B732486|Nr. 74EFC1F9-747D-4867-B951-EFCF29F51AF7|-|-|
|Office Shared|Nr. 64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4|6A174BDB-0049-4D1C-86EF-3114CB0C4C4E|Nr. 76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05|Nr. 625F5772-C1B3-497E-8ABE-7254EDB00506|Nr. 625F5772-C1B3-497E-8ABE-7254EDB00506|
|Project|Nr. 957A4EC0-E67B-4E86-A383-6AF7270B216A|Nr. 1C50E422-24FA-44A9-A120-E88280C8C341|Nr. 706D7F44-8231-489D-9B25-3025ADE9F114|Nr. 107BCD9A-F1DC-4004-A444-33706FC10058|Nr. 107BCD9A-F1DC-4004-A444-33706FC10058|

  ![Screenshot der Final-Startbedingungen](media/setup-project-figure-11.jpg)

  **Abbildung 11: Endgültige Startbedingungen**

Sie können die Startbedingungen für die ExcelAddIn-Installation weiter verfeinern. Beispielsweise ist es möglicherweise sinnvoll, zu überprüfen, ob die eigentliche Office-Zielanwendung installiert ist.

### <a name="to-build-the-setup-project"></a>So erstellen Sie das Setupprojekt

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das **OfficeAddInSetup-Projekt,** und klicken Sie auf **Erstellen**.
2. Navigieren Sie mit **Windows Explorer**zum Ausgabeverzeichnis des **OfficeAddInSetup-Projekts,** und wechseln Sie je nach ausgewählter Buildkonfiguration zum Ordner Release oder Debug. Kopieren Sie alle Dateien aus dem Ordner an einen Speicherort, auf den Benutzer zugreifen können.

So testen Sie das ExcelAddIn-Setup

1. Navigieren Sie zu dem Speicherort, an den Sie **OfficeAddInSetup** kopiert haben.
2. Doppelklicken Sie auf die Datei setup.exe, um das **OfficeAddInSetup-Add-In** zu installieren. Akzeptieren Sie alle angezeigten Softwarelizenzbedingungen, und schließen Sie den Setup-Assistenten ab, um das Add-In auf dem Benutzercomputer zu installieren.

Die Excel Office-Lösung sollte von dem während der Installation angegebenen Speicherort installiert und ausgeführt werden.

## <a name="additional-requirements-for-document-level-solutions"></a>Zusätzliche Anforderungen an Lösungen auf Dokumentebene

Die Bereitstellung von Lösungen auf Dokumentebene erfordert einige verschiedene Konfigurationsschritte im Windows Installer-Setupprojekt.

Im Folgenden finden Sie eine Liste der grundlegenden Schritte, die zum Bereitstellen einer Lösung auf Dokumentebene erforderlich sind:

- Erstellen Sie das Visual Studio-Setupprojekt.
- Fügen Sie die primäre Ausgabe Ihrer Lösung auf Dokumentebene hinzu. Die primäre Ausgabe enthält auch das Microsoft Office-Dokument.
- Fügen Sie die Bereitstellungs- und Anwendungsmanifeste als lose Dateien hinzu.
- Schließen Sie die abhängigen Komponenten aus dem Installationspaket aus (mit Ausnahme von Dienstprogrammassemblys).
- Konfigurieren Sie erforderliche Pakete.
- Konfigurieren Sie die Startbedingungen.
- Erstellen Sie das Setupprojekt, und kopieren Sie die Ergebnisse an den Bereitstellungsort.
- Stellen Sie die Lösung auf Dokumentebene auf dem Benutzercomputer bereit, indem Sie das Setup ausführen.
- Aktualisieren Sie bei Bedarf die benutzerdefinierten Dokumenteigenschaften.

### <a name="changing-the-location-of-the-deployed-document"></a>Ändern des Speicherorts des bereitgestellten Dokuments

Eigenschaften in einem Office-Dokument werden verwendet, um Lösungen auf Dokumentebene zu finden. Wenn das Dokument im gleichen Ordner wie die VSTO-Assembly installiert ist, sind keine Änderungen erforderlich. Wenn es jedoch in einem anderen Ordner installiert ist, müssen diese Eigenschaften während der Installation aktualisiert werden.

Weitere Informationen zu diesen Dokumenteigenschaften finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](custom-document-properties-overview.md).

Um diese Eigenschaften zu ändern, müssen Sie während der Einrichtung eine benutzerdefinierte Aktion verwenden.

Im folgenden Beispiel wird eine Projektmappe auf Dokumentebene namens ExcelWorkbookProject und ein Setupprojekt namens ExcelWorkbookSetup verwendet. Das ExcelWorkbookSetup-Projekt wird mit den oben beschriebenen Schritten konfiguriert, mit Ausnahme des Festlegens der Registrierungsschlüssel.

So fügen Sie das benutzerdefinierte Aktionsprojekt zu Ihrer Visual Studio-Lösung hinzu

1. Hinzufügen eines neuen .NET Console-Projekts zur Projektmappe, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das **Office Document Deployment Project** klicken.
2. Erweitern **Hinzufügen** und Klicken Sie auf **Neues Projekt**.
3. Wählen Sie die Konsolen-App-Vorlage aus, und nennen Sie das Projekt **AddCustomizationCustomAction**.

    ![Screenshot des Projektmappen-Explorers - AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Abbildung 12: Projektmappen-Explorer - AddCustomizationCustomAction**

4. Fügen Sie diesen Assemblys einen Verweis hinzu:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft.VisualStudio.Tools.Anwendungen
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Kopieren Sie diesen Code in Program.cs oder Program.vb

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

Um die Anpassung zum Dokument hinzuzufügen, benötigen Sie die Lösungs-ID Ihrer VSTO-Lösung auf Dokumentebene. Dieser Wert wird aus der Visual Studio-Projektdatei abgerufen.

So rufen Sie die Lösungs-ID ab

1. Klicken Sie im Menü **Erstellen** auf **Lösung erstellen,** um die Projektmappe auf Dokumentebene zu erstellen und der Projektmappen-ID-Eigenschaft die Projektmappen-ID-Eigenschaft hinzuzufügen.
2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt **ExcelWorkbookProject** auf Dokumentebene
3. Klicken Sie auf **UnloadProject,** um von Visual Studio aus auf die Projektdatei zuzugreifen.

    ![Screenshot des Lösungs-Explorers zum Entladen der Excel-Dokumentlösung](media/setup-project-figure-16.jpg)

    **Abbildung 13: Entladen der Excel-Dokumentlösung**

4. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **ExcelWorkbookProject** und klicken Sie auf **EditExcelWorkbookProject.vbproj** oder **Edit ExcelWorkbookProject.csproj**.
5. Suchen Sie im **ExcelWorkbookProject-Editor** das **SolutionID-Element** innerhalb des **PropertyGroup-Elements.**
6. Kopieren Sie den GUID-Wert dieses Elements.

    ![Abrufen der SolutionID](media/setup-project-figure-17.jpg)

    **Abbildung 14: Abrufen der SolutionID**

7. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **ExcelWorkbookProject,** und klicken Sie auf **Projekt neu laden**.
8. Klicken Sie im Dialogfeld auf **Ja,** das angezeigt wird, um den **ExcelWorkbookProject-Editor** zu schließen.
9. Die **Lösungs-ID** wird in der benutzerdefinierten Aktion Installieren verwendet.

Der letzte Schritt besteht darin, die benutzerdefinierte Aktion für die Schritte **Installieren** und **Deinstallieren** zu konfigurieren.

### <a name="to-configure-the-setup-project"></a>So konfigurieren Sie das Setupprojekt

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **ExcelWorkbookSetup**, erweitern **Sie Hinzufügen** und klicken Sie auf **Projektausgabe**.
2. Klicken Sie im Dialogfeld **Projektausgabegruppe hinzufügen** in der **Liste Projekt** auf **AddCustomizationCustomAction**.
3. Wählen Sie **Primäre Ausgabe** aus, und klicken Sie auf **OK,** um das Dialogfeld zu schließen und die Assembly mit der benutzerdefinierten Aktion zum Setupprojekt hinzuzufügen.

    ![Screenshot der benutzerdefinierten Dokumentmanifestaktion - Fenster Projektausgabegruppe hinzufügen](media/setup-project-figure-18.jpg)

    **Abbildung 15: Benutzerdefinierte Aktion des Dokumentmanifests - Projektausgabegruppe hinzufügen**

4. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **ExcelWorkbookSetup**.
5. Erweitern Sie **view,** und klicken Sie auf **Benutzerdefinierte Aktionen**.
6. Klicken Sie im Editor **"Benutzerdefinierte Aktionen" (ExcelWorkbookSetup)** mit der rechten Maustaste auf **Benutzerdefinierte Aktionen,** und klicken Sie auf **Benutzerdefinierte Aktion hinzufügen**.
7. Klicken Sie im Dialogfeld **Element im Projekt** auswählen in der Liste **Suchen** in auf **Anwendungsordner**. Wählen Sie **Primäre Ausgabe aus AddCustomizationCustomAction(active)** aus, und klicken Sie auf **OK,** um die benutzerdefinierte Aktion zum Installationsschritt hinzuzufügen.
8. Klicken Sie unter Knoten **installieren**mit der rechten Maustaste **auf Primäre Ausgabe aus AddCustomizationCustomAction(Active)**, und klicken Sie auf **Umbenennen**. Benennen Sie die benutzerdefinierte Aktion **Dokument zu Eigene Dokumente kopieren, und fügen Sie anpassung an.**
9. Klicken Sie unter dem **Knoten deinstallieren**mit der rechten Maustaste **auf Primäre Ausgabe aus AddCustomizationCustomAction(Active)** und klicken Sie auf **Umbenennen**. Benennen Sie die benutzerdefinierte Aktion **Dokument aus dem Ordner "Dokumente**entfernen".

    ![Screenshot des Fensters Benutzerdefinierte Aktionen des Dokumentmanifests](media/setup-project-figure-19.jpg)

    **Abbildung 16: Benutzerdefinierte Dokumentmanifestaktionen**

10. Klicken Sie im Editor **"Benutzerdefinierte Aktionen" (ExcelWorkbookSetup)** mit der rechten Maustaste auf **Dokument zu Eigenen Dokumenten kopieren, anpassen Sie die Anpassung** an, und klicken Sie auf **Eigenschaftenfenster**.
11. Geben Sie im Fenster **CustomActionData-Eigenschaften** **Properties** den Speicherort der Anpassungs-DLL, das Bereitstellungsmanifest und den Speicherort des Microsoft Office-Dokuments ein. Die SolutionID wird ebenfalls benötigt.
12. Wenn Sie Setupfehler in einer Datei protokollieren möchten, fügen Sie einen LogFile-Parameter ein.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Screenshot des Fensters "Benutzerdefinierte Aktion zum Kopieren von Dokumenten in Meine Dokumente"](media/setup-project-figure-20.jpg)

    **Abbildung 17: Benutzerdefinierte Aktion zum Kopieren von Dokumenten in eigene Dokumente**

13. Die benutzerdefinierte Aktion für Deinstallation benötigt den Namen des Dokuments, Sie können dies mithilfe des gleichen documentLocation-Parameters in **CustomActionData** bereitstellen.

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Kompilieren und Bereitstellen des **ExcelWorkbookSetup-Projekts.**
15. Suchen Sie im Ordner **Eigene Dateien,** und öffnen Sie die Datei ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Weitere Ressourcen

[Gewusst wie: Installieren der Visual Studio-Tools für Office-Runtime](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Primäre Interopassemblys in Office](office-primary-interop-assemblies.md)

[Registrierungseinträge für VSTO-Add-Ins](registry-entries-for-vsto-add-ins.md)

[Übersicht über benutzerdefinierte Dokumenteigenschaften](custom-document-properties-overview.md)

[Angeben von Formularbereichen in der Windows-Registrierung](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Über die Autoren

Wouter van Vugt ist Microsoft MVP mit Office Open XML-Technologien und ein unabhängiger Berater, der sich auf die Erstellung von Office Business Applications (OBAs) mit SharePoint, Microsoft Office und verwandten .NET-Technologien konzentriert.
Wouter ist ein häufiger Mitwirkender von Entwicklercommunity-Sites wie [OpenXmlDeveloper.org](http://openxmldeveloper.org/) und [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Er hat mehrere White Papers und Artikel sowie ein Buch veröffentlicht, das online mit dem Titel Open XML: Explained e-book verfügbar ist.
Wouter ist Gründer von Code-Counsel, einem niederländischen Unternehmen, das sich auf die Bereitstellung modernster technischer Inhalte über eine Vielzahl von Kanälen konzentriert. Sie können mehr über Wouter erfahren, indem Sie seinen Blog lesen und die [Code-Counsel-Website](http://www.code-counsel.net/)besuchen.

Ted Pattison ist SharePoint MVP, Autor, Trainer und Gründer der Ted Pattison Group. Im Herbst 2005 wurde Ted von der Entwicklerplattform-Evangelism-Gruppe von Microsoft mit dem Erstellen des Ascend-Entwicklerschulungscurriculums für Windows SharePoint Services 3.0 und Microsoft Office SharePoint Server 2007 beauftragt. Seitdem konzentriert sich Ted ganz auf die Schulung professioneller Entwickler über SharePoint 2007-Technologien. Ted hat das Schreiben eines Buches für Microsoft Press mit dem Titel Inside Windows SharePoint Services 3.0 abgeschlossen, das sich auf die Verwendung von SharePoint als Entwicklungsplattform für die Erstellung von Geschäftslösungen konzentriert. Ted schreibt auch eine entwicklerorientierte Kolumne für das MSDN Magazine mit dem Titel Office Space.
