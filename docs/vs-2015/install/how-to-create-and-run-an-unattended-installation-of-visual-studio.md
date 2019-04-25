---
title: 'Gewusst wie: Erstellen und Ausführen einer unbeaufsichtigten Installation | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: deabd34896b327f7cbbb35c7af75f5810dcfbf17
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040545"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Gewusst wie: Erstellen und Ausführen einer unbeaufsichtigten Installation von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Installationsanwendung für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] als unbeaufsichtigte Installation (d. h. benutzerdefinierte automatische Installation) über ein Intranet anstatt von Medien wie DVDs ausführen. In diesem Thema wird erläutert, wie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auf die Installation von einer Netzwerkfreigabe vorbereitet wird.

## <a name="creating-a-network-image"></a>Erstellen eines Netzwerkabbilds
 Erstellen Sie zuerst ein Netzwerkabbild der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Medien.

#### <a name="to-create-a-network-image"></a>So erstellen Sie ein Netzwerkabbild

1. Erstellen Sie einen Ordner auf dem Server (z.B. *Laufwerk*:\IDEinstall\\).

2. Laden Sie das Installationsprogramm von [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) herunter und führen Sie dann *Product*.exe /Layout *Drive*:\IDEinstall\ aus.

3. Geben Sie den Ordner „IDEinstall“ im Netzwerk frei, und legen Sie dann die entsprechenden Sicherheitseinstellungen fest.

     Der Netzwerkpfad der Installationsanwendung für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entspricht \\\\*ServerName*\IDEinstall\\*Product*.exe.

    > [!NOTE]
    >  Die Installation schlägt möglicherweise fehl, wenn eine Pfad- und Dateinamenkombination 260 Zeichen überschreitet. Die maximale Länge eines Pfads in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] beträgt 221 Zeichen.  Der Name des lokalen Pfads sollte 70 Zeichen nicht überschreiten, und der Name des Netzwerkpfads sollte 39 Zeichen nicht überschreiten.

     Bei der Installation treten möglicherweise auch dann Fehler auf, wenn die Ordnernamen im Pfad eingebettete Leerzeichen aufweisen (beispielsweise „\\\\*ServerName*\IDE install“ oder „\\\\*ServerName*\Visual Studio\\“).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Bereitstellen von Visual Studio im unbeaufsichtigten Modus
 Zum Bereitstellen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im unbeaufsichtigten Modus müssen Sie die Datei „AdminDeployment.xml“ ändern. Dafür müssen Sie die Datei „AdminDeployment.xml“ erstellen, indem Sie den Befehlszeilenparameter `/CreateAdminFile` *\<<Dateispeicherort>* verwenden. Mit dieser Datei können Sie dann entweder eine Bereitstellung von Visual Studio mithilfe von Push in das Netzwerk übertragen oder die Datei mithilfe von Pull in eine Installation übertragen, wenn Sie die Datei in das Verzeichnis " *Laufwerk*:\IDEinstall\packages" einfügen. Die Datei AdminDeployment.xml ist nicht spezifisch für ein Betriebssystem, eine Architektur, eine Edition von Visual Studio oder eine Betriebssystemsprache.

> [!CAUTION]
>  In manchen Fällen werden Elemente, die in der Datei "AdminDeployment.xml" als ausgewählt aufgeführt sind, nicht installiert. Um dieses Problem zu beheben, platzieren sie die mit "Selected="yes"" markierten Elemente am **Ende** der Datei "AdminDeployment.xml".
>
>  Wenn Sie die optionalen Abhängigkeiten eines Elements nicht installieren möchten, müssen Sie zuerst das übergeordnete Element auswählen und dann die Auswahl der optionalen Abhängigkeiten nach dem übergeordneten Element aufheben, wie im folgenden Screenshot gezeigt:
>
>  ![Installationselemente am Ende der AdminDeployment.xml-Datei ](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
>  Eine weitere Möglichkeit besteht darin, die optionalen untergeordneten Elemente eines übergeordneten Elements einfach auszuschließen, d. h., keine mit "Selected="no"" markierten Elemente einzuschließen. Allerdings müssen alle Elemente mit "Selected="yes"" weiterhin am Ende der Datei "AdminDeployment.xml" platziert werden.

> [!IMPORTANT]
>  Während der Installation startet der Computer möglicherweise mehrere Male erneut. Nach dem Neustart müssen Sie zum Ausführen der Installation sich wieder mit demselben Benutzerkonto anmelden, mit dem Sie angemeldet waren, bevor der Computer neu gestartet wurde. Automatische Neustarts können vermieden werden, indem die erforderlichen Komponenten vor dem Ausführen einer unbeaufsichtigten Installation vorinstalliert werden. Weitere Informationen finden Sie im Abschnitt: "Vermeiden eines Neustarts während des Setups" im [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

 Das AdminDeployment-Dateischema enthält die folgenden Elemente:

|Element|Attribut|Werte|Beschreibung|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Pfad*|Identisches Verhalten wie beim Überschreiben eines Pfades in der Benutzeroberfläche der Installationsanwendung. Dieses Element wird ignoriert, wenn Visual Studio bereits installiert ist.|
|BundleCustomizations|NoWeb|yes&#124;default|Wenn der Wert dieses Elements "Ja" lautet, versucht die Installationsanwendung nie, während der Setupaktion ins Internet zu wechseln.|
|SelectableItemCustomization|Hidden|Ja&#124;Nein|Wenn der Wert dieses Elements "Ja" lautet, wird ein wählbares Element in der Anpassungsstruktur ausgeblendet.|
|SelectableItemCustomization|Ausgewählt|Ja&#124;Nein|Wählt ein wählbares Element in der Anpassungsstruktur aus oder löscht dieses.|
|BundleCustomizations|Feed|Pfad|Speicherort des Feeds, den der Benutzer verwenden möchte.  Dieser Feed wird für nachfolgende Änderungsvorgänge auf dem Computer verwendet (standardmäßig "Default").|
|BundleCustomizations|SuppressRefreshPrompt|yes&#124;default|Verhindert, dass der Benutzer aufgefordert wird, das Setup zu aktualisieren, wenn eine neuere Version verfügbar ist.|
|BundleCustomizations|NoRefresh|yes&#124;default|Das Setup wird nicht aktualisiert, wenn eine neuere Version verfügbar ist.|
|BundleCustomizations|NoCacheOnlyMode|yes&#124;default|Verhindert, dass der Paket-Cache vorab gefüllt wird.|

> [!WARNING]
>  Die Installationsanwendung berücksichtigt den Auswahlzustand eines auswählbaren Elements, selbst wenn es ausgeblendet ist. Wenn Sie beispielsweise ein wählbares Element immer installieren möchten, können Sie es als ausgeblendet und ausgewählt markieren.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Erstellen einer unbeaufsichtigten Installation von Visual Studio

1. Ändern Sie in der Datei „ *Laufwerk*:\IDEinstall\AdminDeployment.xml“ den Wert des „NoWeb“-Attributs des „BundleCustomizations“-Elements von „default“ in „yes“, wie im folgenden Beispiel gezeigt:

     Ändern Sie `<BundleCustomizations TargetDir="default" NoWeb="default"/>` in `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2. Ändern Sie das SelectableItemCustomizations-Attribut ggf. für optionale Komponenten, und speichern Sie die Datei.

## <a name="running-unattended-setup"></a>Ausführen der unbeaufsichtigten Installation
 Sie können eine unbeaufsichtigte Installation ausführen, indem Sie die Installationsanwendung für Visual Studio entweder automatisch auf Clientcomputern ausführen oder indem Sie zulassen, dass Benutzer die Anwendung selbst mit Einstellungen auszuführen, die Sie definieren.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Ausführen einer unbeaufsichtigten Installation auf einem Clientcomputer

- Öffnen Sie das Menü **Start**, wählen Sie **Ausführen**, und geben Sie dann \\\\*ServerName*\IDEinstall\vs_*Product*.exe /adminfile *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em> ein.

   Beispielsweise können Sie die folgende Befehlszeile angeben: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Aktivieren von Clients, um Visual Studio mit vordefinierten Einstellungen manuell zu installieren

1. Kopieren Sie die benutzerdefinierte Datei „AdminDeployment.xml“ in eine schreibgeschützte Netzwerkfreigabe (beispielsweise „\\\\*ServerName*\IDEinstall\packages\AdminDeployment.xml“).

2. Aktivieren Sie Benutzer für die Installation von dieser Freigabe.

## <a name="maintaining-an-installation"></a>Verwalten einer Installation
 Wenn Sie **Systemsteuerung** öffnen und die Installationsanwendung erneut ausführen, können Sie Funktionen von Visual Studio ändern, Programmiersprachen deinstallieren und Visual Studio reparieren bzw. deinstallieren.

> [!NOTE]
>  Sie müssen über Administratoranmeldeinformationen auf dem lokalen Computer verfügen, um den Wartungsmodus zu verwenden.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Verwalten einer Installation auf einem Clientcomputer

- Öffnen Sie **Systemsteuerung**, und wählen Sie dann **Programme und Funktionen**aus.

- Wählen Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]und dann **Ändern**aus.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Ändern der AdminDeployment-Einstellungen auf einem Clientcomputer nach der Installation von Visual Studio

1. Aktualisieren Sie ggf. "AdminDeployment.xml".

2. Öffnen Sie das Menü **Start** , und wählen Sie dann **Ausführen**aus.

3. Geben Sie den folgenden Text ein: \\\\*ServerName*\IDEinstall\vs_*Product*.exe /AdminFile PathToAdmindeployment.xml File

    AdditionalParametersAsNeeded

    Beispielsweise können Sie die folgende Befehlszeile angeben: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   "Reparieren" ist der Standardparameter nach der Installation von Visual Studio. Wenn Sie Visual Studio mit aktualisierter /AdminFile reparieren, überschreiben Sie die aktuellen Administrator-Bereitstellungs-Einstellungen mit den Einstellungen, die die aktualisierte Datei „AdminDeployment.xml“ aufruft.

## <a name="updating-an-installation"></a>Aktualisieren einer Installation
 Microsoft hat mehrere Updates für Visual Studio 2015 veröffentlicht. In diesem Abschnitt wird erläutert, wie Sie Ihr unbeaufsichtigtes Installationsimage von Visual Studio 2015 aktualisieren, damit es die Updates enthält.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>So aktualisieren Sie eine unbeaufsichtigte Installation von Visual Studio

1. Suchen Sie die Datei „Product.exe“ im vorhandenen Netzwerkimage, klicken Sie mit der rechten Maustaste darauf, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Details**, und notieren Sie sich dann die Eigenschaft **Produktversion**.

    ![Beispiel des Dialogfelds „Eigenschaften“ in einer unbeaufsichtigten Installation von Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG " Unbeaufsichtigte Installation – Dialogfeld „Eigenschaften“")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Wenn die Produktversion 14.0.24720.0 oder 14.0.24720.1 ist, gehen Sie wie folgt vor:
   1. Führen Sie *Product.exe* /Layout *Drive:* \IDEinstall auf einem Computer mit Internetanschluss aus. (Führen Sie zum Beispiel `vs_enterprise.exe /Layout d:\IDEinstall` aus.)

   2. Nachdem das /Layout abgeschlossen ist, kopieren Sie das neue Image an einen neuen Speicherort.

   3. Erstellen und Ändern Sie die Datei „AdminDeployment.xml“. Verwenden Sie hierzu den Befehlszeilenparameter `/CreateAdminFile`*\<Dateispeicherort >*. (Weitere Informationen finden Sie im Abschnitt „Bereitstellen von Visual Studio im unbeaufsichtigten Modus“ in diesem Artikel.)

   4. Führen Sie auf dem Clientcomputer den folgenden Befehl aus, um die Kopie von Visual Studio zu aktualisieren, die Sie zuvor installiert haben: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart".

        Führen Sie zum Beispiel `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart` aus.
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Gehen Sie für andere Produktversionswerte folgendermaßen vor:
   1. Führen Sie *Product.exe* /Layout *Drive:* \IDEinstall auf einem Computer mit Internetanschluss aus. (Führen Sie zum Beispiel `vs-enterprise.exe /Layout d:\IDEinstall` aus.)

   2. Nachdem das /Layout abgeschlossen ist, kopieren Sie das neue Image an einen neuen Speicherort. (Oder Sie können stattdessen das bestehende Netzwerkimage überschreiben.)

   3. Erstellen Sie die Datei „AdminDeployment.xml“ und ändern Sie sie dann. Verwenden Sie hierzu den Befehlszeilenparameter `/CreateAdminFile`*\<Dateispeicherort >*. (Weitere Informationen finden Sie im Abschnitt „Bereitstellen von Visual Studio im unbeaufsichtigten Modus“ in diesem Artikel.)

   4. Wenn Sie das Image an einen neuen Speicherort kopieren, müssen Sie den folgenden Befehl auf dem Clientcomputer ausführen, um die Kopie von Visual Studio zu aktualisieren, die Sie zuvor installiert haben: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart".

        Führen Sie zum Beispiel `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart` aus.

   5. Wenn Sie das vorhandene Netzwerkimage überschreiben, können Sie den Befehl wie im vorherigen Schritt beschrieben ausführen oder wie folgt vorgehen:
       1. Öffnen Sie **Systemsteuerung**, und wählen Sie dann **Programme und Funktionen**aus.

       2. Wählen Sie **Visual Studio** und dann **Ändern** aus.

       3. Nachdem Visual Studio im Wartungsmodus gestartet wurde, klicken Sie auf **Ändern**.

       4. Auf der Seite „Features“ wird das aktuelle Update angezeigt. Wählen Sie die anderen Features, die Sie installieren möchten, klicken Sie auf **Weiter** und dann auf **Update**, um sowohl das Update als auch die neuen Features zu installieren.

## <a name="registering-the-product"></a>Registrieren des Produkts
 Nachdem die Installation abgeschlossen ist, können Sie Ihre Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aus [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]heraus registrieren.

#### <a name="to-register"></a>Zum Registrieren führen Sie Folgendes aus:

1. Öffnen Sie das Menü **Hilfe** , und wählen Sie dann die Option **Produkt registrieren**aus.

2. Geben Sie den Product Key ein.

     (Weitere Informationen finden Sie in den Themen [Gewusst wie: Suchen des Visual Studio Product Key](../install/how-to-locate-the-visual-studio-product-key.md) und [Vorgehensweise: Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).)

## <a name="see-also"></a>Siehe auch
 [Installieren von Visual Studio](../install/install-visual-studio-2015.md)