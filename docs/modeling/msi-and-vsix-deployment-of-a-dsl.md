---
title: MSI- und VSIX-Bereitstellung einer DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0c17ac476e0edbec73c407090cd84e6a44d9219c
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>MSI- und VSIX-Bereitstellung einer DSL
Sie können eine domänenspezifische Sprache auf Ihrem eigenen Computer oder auf anderen Computern installieren. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muss bereits auf dem Zielcomputer installiert werden.

##  <a name="which"></a> Auswählen zwischen VSIX-als auch MSI-Bereitstellung
 Es gibt zwei Methoden zum Bereitstellen einer domänenspezifischen Sprache:

|Methode|Vorteile|
|------------|--------------|
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterung)|Sehr leicht bereitzustellen: Kopieren und Ausführen der **VSIX** Datei aus dem Projekt DslPackage.<br /><br /> Weitere Informationen finden Sie unter [installieren und Deinstallieren eine DSL mit der VSX](#Installing).|
|MSI-Datei (Installer-Datei)|– Ermöglicht es den Benutzer, öffnen Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] durch Doppelklicken auf einen DSL-Datei.<br />-Der DSL-Dateityp in der Zielcomputer ein Symbol zugeordnet.<br />-Ordnet XSD (XML Schema) mit der DSL-Dateityp an. Dies vermeidet Warnungen beim Laden der das in den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> Sie müssen ein Setup-Projekt zur Projektmappe so erstellen eine MSI-Datei hinzufügen.<br /><br /> Weitere Informationen finden Sie unter [DSL mithilfe einer MSI-Datei bereitstellen](#msi).|

##  <a name="Installing"></a> Installieren und deinstallieren mithilfe der VSX DSL
 Wenn von dieser Methode der DSL installiert ist, kann der Benutzer innerhalb eine DSL-Datei öffnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aber die Datei kann nicht aus dem Windows-Explorer nicht geöffnet werden.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Eine DSL mit der VSX installieren

1.  Suchen Sie auf dem Computer die **VSIX** -Datei, die vom Paket DSL-Projekt erstellt wurde.

    1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **DslPackage** Projekt, und klicken Sie dann auf **Ordner in Windows Explorer öffnen**.

    2.  Suchen Sie die Datei **"bin"\\\*\\***IhrProjekt***. DslPackage.vsix**

2.  Kopieren der **VSIX** Datei auf den Zielcomputer, auf denen der DSL installiert werden soll. Dies kann Ihr eigener Computer oder ein anderer Computer sein.

    -   Die Zielcomputer müssen eine der Editionen von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , konzentriert zur Laufzeit unterstützt. Weitere Informationen finden Sie unter [unterstützten Editionen von Visual Studio Visualization & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    -   Die Zielcomputer müssen eine der Editionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im angegebenen **DslPackage\source.extensions.manifest**.

3.  Doppelklicken Sie auf dem Zielcomputer auf die **VSIX** Datei.

     **Installer für Visual Studio-Erweiterungen** wird geöffnet, und die Erweiterung wird installiert.

4.  Starten Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], bzw. starten Sie die Anwendung neu.

5.  Verwenden Sie zum Testen der DSL [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Erstellen einer neuen Datei mit der Erweiterung, die Sie für Ihre DSL definiert.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Eine DSL deinstallieren, die mithilfe von VSX installiert wurde

1.  Auf der **Tools** Menü klicken Sie auf **Erweiterungs-Manager**.

2.  Erweitern Sie **Installierte Erweiterungen**.

3.  Wählen Sie die Erweiterung in der der DSL definiert ist, und klicken Sie dann auf **Deinstallieren**.

 In seltenen Fällen kann es vorkommen, dass eine fehlerhafte Erweiterung nicht geladen und ein Bericht im Fehlerfenster erstellt wird, aber im Erweiterungs-Manager keine Informationen angezeigt werden. Sie haben die Möglichkeit, die Erweiterung zu entfernen, indem Sie die Datei aus dem folgenden Ordner löschen:

 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

##  <a name="msi"></a> Eine DSL in eine MSI-Datei bereitstellen
 Durch die Definition einer MSI-Datei (Windows Installer)-Datei für Ihre DSL, können Sie Benutzern das Öffnen von DSL-Dateien aus Windows Explorer zulassen. Sie können auch ein Symbol und eine kurze Beschreibung mit der Dateinamenerweiterung zuordnen. Darüber hinaus kann die MSI-Datei XSD-Code installieren, die zur Validierung der DSL-Dateien verwendet werden kann. Wenn Sie möchten, können Sie andere Komponenten in die MSI-Datei hinzufügen, die zur selben Zeit installiert werden.

 Weitere Informationen zur MSI-Dateien und anderen Bereitstellungsoptionen finden Sie unter [Bereitstellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md).

 Um eine MSI-Datei zu erstellen, die Sie Hinzufügen eines Setup-Projekts, um Ihre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung. Die einfachste Methode zum Erstellen eines Setupprojekts ist, die Vorlage CreateMsiSetupProject.tt verwenden, das Sie herunterladen können die [VMSDK Standort](http://go.microsoft.com/fwlink/?LinkID=186128).

#### <a name="to-deploy-a-dsl-in-an-msi"></a>Eine DSL in eine MSI-Datei bereitstellen.

1.  Legen Sie `InstalledByMsi` in der Erweiterungsmanifest. Dadurch wird verhindert, dass die VSX installiert und mit Ausnahme von der MSI-Datei deinstalliert werden. Dies ist wichtig, wenn Sie andere Komponenten in die MSI-Datei umfasst.

    1.  Öffnen Sie DslPackage\source.extension.tt

    2.  Fügen Sie die folgende Zeile vor `<SupportedProducts>`:

        ```
        <InstalledByMsi>true</InstalledByMsi>
        ```

2.  Erstellen Sie oder bearbeiten Sie ein Symbol, das der DSL in Windows Explorer dargestellt wird. Bearbeiten Sie z. B. **DslPackage\Resources\File.ico**

3.  Stellen Sie sicher, dass die folgenden Attribute von der DSL richtig sind:

    -   Klicken Sie auf den Stammknoten, und überprüfen Sie im Eigenschaftenfenster, im Explorer für DSL:

        -   Beschreibung

        -   Version

    -   Klicken Sie auf die **Editor** Knoten, und klicken Sie im Fenster Eigenschaften auf **Symbol**. Legen Sie den Wert auf eine Symboldatei in verweisen **DslPackage\Resources**, wie z. B. **File.ico**

    -   Auf der **erstellen** öffnen Sie im Menü **Configuration Manager**, und wählen Sie die Konfiguration, die Sie erstellen z. B., möchten **Release** oder **Debuggen** .

4.  Wechseln Sie zu [Visualization and Modeling SDK-Startseite](http://go.microsoft.com/fwlink/?LinkID=186128), und von der **Downloads** Registerkarte, zum Downloadpfad **CreateMsiSetupProject.tt**.

5.  Hinzufügen **CreateMsiSetupProject.tt** dem Dsl-Projekt.

     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt eine Datei namens **CreateMsiSetupProject.vdproj**.

6.  Kopieren Sie im Windows-Explorer Dsl\\\*.vdproj in einen neuen Ordner mit dem Namen Setup.

     (Wenn Sie möchten, können Sie jetzt CreateMsiSetupProject.tt aus Ihrem Dsl-Projekt ausschließen.)

7.  In **Projektmappen-Explorer**, hinzufügen **Setup\\\*.vdproj** wie ein vorhandenes Projekt.

8.  Auf der **Projekt** Menü klicken Sie auf **Projektabhängigkeiten**.

     In der **Projektabhängigkeiten** Dialogfeld wählen die Setup-Projekt.

     Aktivieren Sie das Kontrollkästchen neben **DslPackage**.

9. Generieren Sie die Projektmappe neu.

10. Suchen Sie im Windows-Explorer erstellte MSI-Datei im Setup-Projekt aus.

     Kopieren Sie die MSI-Datei auf einem Computer, auf dem der DSL installiert werden soll. Doppelklicken Sie auf die MSI-Datei. Das Installationsprogramm wird ausgeführt.

11. Erstellen Sie eine neue Datei mit der Erweiterung der DSL, in dem Zielcomputer. Überprüfen Sie, ob:

    -   In Windows Explorer-Listenansicht wird die Datei angezeigt, mit dem Symbol und eine Beschreibung ein, die Sie definiert.

    -   Wenn Sie die Datei doppelklicken [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] beginnt, und die DSL-Datei in Ihrem DSL-Editor geöffnet.

 Falls gewünscht, können Sie das Setup-Projekt manuell erstellen, anstelle der Vorlage "Text". Eine exemplarische Vorgehensweise, die diese Prozedur umfasst finden Sie in Kapitel 5 die [Visualization and Modeling SDK Lab](http://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>So deinstallieren Sie eine DSL, die über eine MSI-Datei installiert wurde

1.  Öffnen Sie in Windows die **Programme und Funktionen** Systemsteuerung.

2.  Deinstallieren der DSL.

3.  Starten Sie Visual Studio neu.