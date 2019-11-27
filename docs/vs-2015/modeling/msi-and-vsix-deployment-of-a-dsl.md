---
title: MSI-und VSIX-Bereitstellung einer DSL | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4917fc81f439ef0185a753fb1c4c85e460eb7681
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297736"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>MSI- und VSIX-Bereitstellung einer DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine domänenspezifische Sprache auf Ihrem eigenen Computer oder auf anderen Computern installieren. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] müssen bereits auf dem Zielcomputer installiert sein.

## <a name="which"></a>Auswählen zwischen VSIX und MSI-Bereitstellung
 Es gibt zwei Methoden zum Bereitstellen einer domänenspezifischen Sprache:

|Methode|Vorteile|
|------------|--------------|
|VSX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Erweiterung)|Einfache Bereitstellung: Kopieren Sie die **VSIX** -Datei, und führen Sie Sie aus dem dslpackage-Projekt aus.<br /><br /> Weitere Informationen finden [Sie unter Installieren und Deinstallieren einer DSL mithilfe von VSX](#Installing).|
|MSI (Installerdatei)|: Ermöglicht dem Benutzer das Öffnen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] durch Doppelklicken auf eine DSL-Datei.<br />-Verknüpft ein Symbol mit dem DSL-Dateityp auf dem Zielcomputer.<br />-Ordnet ein XSD-Schema (XML-Schema) dem DSL-Dateityp zu. Dadurch werden Warnungen vermieden, wenn die Datei in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]geladen wird.<br /><br /> Sie müssen der Projekt Mappe ein Setup-Projekt hinzufügen, um eine MSI-Datei zu erstellen.<br /><br /> Weitere Informationen finden Sie unter Bereitstellen [einer DSL mithilfe einer MSI-Datei](#msi).|

## <a name="Installing"></a>Installieren und Deinstallieren einer DSL mithilfe von VSX
 Wenn die DSL durch diese Methode installiert wird, kann der Benutzer eine DSL-Datei in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]öffnen, aber die Datei kann nicht aus Windows-Explorer geöffnet werden.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>So installieren Sie eine DSL mithilfe von VSX

1. Suchen Sie auf Ihrem Computer die **VSIX** -Datei, die von Ihrem DSL-Paket Projekt erstellt wurde.

    1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt **dslpackage** , und klicken Sie dann auf **Ordner in Windows-Explorer öffnen**.

    2. Suchen Sie den Datei- **bin\\\*\\** _yourproject_ **. Dslpackage. vsix**

2. Kopieren Sie die **VSIX** -Datei auf den Zielcomputer, auf dem Sie die DSL installieren möchten. Dies kann Ihr eigener Computer oder ein anderer Computer sein.

    - Der Zielcomputer muss über eine der Editionen von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] verfügen, von denen DSLs zur Laufzeit unterstützt werden. Weitere Informationen finden Sie [unter Unterstützte Visual Studio-Editionen für die Visualisierung & Modellierungs-SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Auf dem Zielcomputer muss eine der Editionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in **DslPackage\source.Extensions.Manifest**angegeben sein.

3. Doppelklicken Sie auf dem Zielcomputer auf die **VSIX** -Datei.

     **Installer für Visual Studio-Erweiterungen** wird geöffnet, und die Erweiterung wird installiert.

4. Starten Sie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], bzw. starten Sie die Anwendung neu.

5. Um die DSL zu testen, verwenden Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], um eine neue Datei mit der Erweiterung zu erstellen, die Sie für Ihre DSL definiert haben.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>So deinstallieren Sie eine mit VSX installierte DSL

1. Klicken Sie **im Menü Extras** auf **Erweiterungs-Manager**.

2. Erweitern Sie **Installierte Erweiterungen**.

3. Wählen Sie die Erweiterung aus, in der die DSL definiert ist, und klicken Sie dann auf **deinstallieren**.

   In seltenen Fällen kann es vorkommen, dass eine fehlerhafte Erweiterung nicht geladen und ein Bericht im Fehlerfenster erstellt wird, aber im Erweiterungs-Manager keine Informationen angezeigt werden. Sie haben die Möglichkeit, die Erweiterung zu entfernen, indem Sie die Datei aus dem folgenden Ordner löschen:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a>Bereitstellen einer DSL in einer MSI
 Indem Sie eine MSI-Datei (Windows Installer) für Ihre DSL definieren, können Sie es Benutzern ermöglichen, DSL-Dateien aus Windows-Explorer zu öffnen. Sie können der Dateinamenerweiterung auch ein Symbol und eine kurze Beschreibung zuordnen. Außerdem kann die MSI eine XSD-Datei installieren, die zum Überprüfen von DSL-Dateien verwendet werden kann. Wenn Sie möchten, können Sie der MSI weitere Komponenten hinzufügen, die gleichzeitig installiert werden.

 Weitere Informationen zu MSI-Dateien und anderen Bereitstellungs Optionen finden Sie unter bereit [Stellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md).

 Zum Erstellen einer MSI fügen Sie der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekt Mappe ein Setup-Projekt hinzu. Die einfachste Methode zum Erstellen eines Setup-Projekts ist die Verwendung der Vorlage CreateMsiSetupProject.tt, die Sie von der [vmsdk-Website](https://go.microsoft.com/fwlink/?LinkID=186128)herunterladen können.

#### <a name="to-deploy-a-dsl-in-an-msi"></a>So stellen Sie eine DSL in einer MSI bereit

1. Legen Sie `InstalledByMsi` im Erweiterungs Manifest fest. Dadurch wird verhindert, dass VSX installiert und deinstalliert wird, mit Ausnahme der MSI-Datei. Dies ist wichtig, wenn Sie andere Komponenten in die MSI einschließen.

   1. DslPackage\source.Extension.tt öffnen

   2. Fügen Sie die folgende Zeile vor dem `<SupportedProducts>`ein:

       ```
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Erstellen oder bearbeiten Sie ein Symbol, das Ihre DSL in Windows-Explorer darstellt. Bearbeiten Sie z. b. **dslpackage\resources\file.ico** .

3. Stellen Sie sicher, dass die folgenden Attribute Ihrer DSL korrekt sind:

   - Klicken Sie im DSL-Explorer auf den Stamm Knoten, und überprüfen Sie in Eigenschaftenfenster Folgendes:

       - Beschreibung

       - Version

   - Klicken Sie auf den **Editor** -Knoten, und klicken Sie im Eigenschaftenfenster auf das **Symbol**. Legen Sie den Wert so fest, dass er auf eine Symbol Datei in **dslpackage\resources**verweist, z **. b. Datei. ico**

   - Öffnen Sie im Menü **Erstellen** die **Configuration Manager**, und wählen Sie die Konfiguration aus, die Sie erstellen möchten, z. b. **Release** oder **Debug**.

4. Wechseln Sie zur [Startseite des Visualisierungs-und Modellierungs-](https://go.microsoft.com/fwlink/?LinkID=186128)SDKs, und laden Sie auf der Registerkarte **Downloads** **CreateMsiSetupProject.tt**herunter

5. Fügen Sie **CreateMsiSetupProject.tt** Ihrem DSL-Projekt hinzu.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt eine Datei namens " **deatemsisetupproject. vdproj**".

6. Kopieren Sie in Windows-Explorer DSL\\*. vdproj in einen neuen Ordner mit dem Namen Setup.

    (Wenn Sie möchten, können Sie jetzt CreateMsiSetupProject.tt aus Ihrem DSL-Projekt ausschließen.)

7. Fügen Sie in **Projektmappen-Explorer**das **Setup\\\*. vdproj** als vorhandenes Projekt hinzu.

8. Klicken Sie im Menü **Projekt** auf **Projekt Abhängigkeiten**.

    Wählen Sie im Dialogfeld **Projekt Abhängigkeiten** das Setup-Projekt aus.

    Aktivieren Sie das Kontrollkästchen neben **dslpackage**.

9. Generieren Sie die Projektmappe neu.

10. Suchen Sie im Windows-Explorer nach der erstellten MSI-Datei in Ihrem Setup-Projekt.

     Kopieren Sie die MSI-Datei auf einen Computer, auf dem Sie die DSL installieren möchten. Doppelklicken Sie auf die MSI-Datei. Das Installationsprogramm wird ausgeführt.

11. Erstellen Sie auf dem Zielcomputer eine neue Datei, die über die Dateierweiterung ihrer DSL verfügt. Überprüfen Sie Folgendes:

    - In der Listenansicht von Windows-Explorer wird die Datei mit dem von Ihnen definierten Symbol und der Beschreibung angezeigt.

    - Wenn Sie auf die Datei doppelklicken, wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gestartet, und die DSL-Datei wird in Ihrem DSL-Editor geöffnet.

    Wenn Sie möchten, können Sie das Setup-Projekt manuell erstellen, anstatt die Textvorlage zu verwenden. Eine exemplarische Vorgehensweise, die diese Vorgehensweise umfasst, finden Sie in Kapitel 5 der SDK-Übungseinheit für [Visualisierung und Modellierung](https://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>So deinstallieren Sie eine von einer MSI installierte DSL

1. Öffnen Sie in Windows die Systemsteuerung **Programme und Funktionen** .

2. Deinstallieren Sie die DSL.

3. Starten Sie Visual Studio neu.
