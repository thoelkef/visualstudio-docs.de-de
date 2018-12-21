---
title: 'Vorgehensweise: Erstellen und Ausführen einer unbeaufsichtigten Installation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: bc1a6ba1a36dd7514257fcbb8ba4c26ca1ee6116
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065518"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Vorgehensweise: Erstellen und Ausführen einer unbeaufsichtigten Installation von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Installationsanwendung für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] als unbeaufsichtigte Installation (d. h. benutzerdefinierte automatische Installation) über ein Intranet anstatt von Medien wie DVDs ausführen. In diesem Thema wird beschrieben, wie vorbereiten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] für diese Art der Installation von einer Netzwerkfreigabe.

## <a name="creating-a-network-image"></a>Erstellen eines Netzwerkabbilds
 Erstellen Sie zuerst ein Netzwerkabbild der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Medien.

#### <a name="to-create-a-network-image"></a>So erstellen Sie ein Netzwerkabbild

1.  Erstellen Sie einen Ordner auf dem Server (z.B. *Laufwerk*:\IDEinstall\\).

2.  Herunterladen des Installationsprogramms von [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015), und führen Sie dann *Produkt*.exe/Layout *Laufwerk*: \IDEinstall\

3.  Geben Sie den Ordner IDEinstall im Netzwerk, und legen Sie dann die entsprechenden Sicherheitseinstellungen fest.

     Der Netzwerkpfad der installationsanwendung für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ähnelt \\ \\ *ServerName*\IDEinstall\\*Produkt*.exe.

    > [!NOTE]
    >  Die Installation schlägt möglicherweise fehl, wenn eine Pfad- und Dateinamenkombination 260 Zeichen überschreitet. Die maximale Länge eines Pfads in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] beträgt 221 Zeichen.  Der Name des lokalen Pfads sollte 70 Zeichen nicht überschreiten, und der Name des Netzwerkpfads sollte 39 Zeichen nicht überschreiten.

     Bei der Installation treten möglicherweise auch dann Fehler auf, wenn die Ordnernamen im Pfad eingebettete Leerzeichen aufweisen (beispielsweise „\\\\*ServerName*\IDE install“ oder „\\\\*ServerName*\Visual Studio\\“).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Bereitstellen von Visual Studio im unbeaufsichtigten Modus
 Zum Bereitstellen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im unbeaufsichtigten Modus müssen Sie die Datei „AdminDeployment.xml“ ändern. Zu diesem Zweck müssen Sie zuerst die Datei "admindeployment.xml" erstellen, mit der `/CreateAdminFile`  *\<Dateispeicherort >* Befehlszeilenparameter. Mit dieser Datei können Sie dann entweder eine Bereitstellung von Visual Studio mithilfe von Push in das Netzwerk übertragen oder die Datei mithilfe von Pull in eine Installation übertragen, wenn Sie die Datei in das Verzeichnis " *Laufwerk*:\IDEinstall\packages" einfügen. Die Datei AdminDeployment.xml ist nicht spezifisch für ein Betriebssystem, eine Architektur, eine Edition von Visual Studio oder eine Betriebssystemsprache.

> [!CAUTION]
>  In manchen Fällen werden Elemente, die in der Datei "AdminDeployment.xml" als ausgewählt aufgeführt sind, nicht installiert. Um dieses Problem zu beheben, platzieren sie die mit "Selected="yes"" markierten Elemente am **Ende** der Datei "AdminDeployment.xml".
>
>  Wenn Sie die optionalen Abhängigkeiten eines Elements nicht installieren möchten, müssen Sie zuerst das übergeordnete Element auswählen und dann die Auswahl der optionalen Abhängigkeiten nach dem übergeordneten Element aufheben, wie im folgenden Screenshot gezeigt:
>
>  ![Installationselemente am Ende der Datei "admindeployment.xml"](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
>  Eine weitere Möglichkeit besteht darin, die optionalen untergeordneten Elemente eines übergeordneten Elements einfach auszuschließen, d. h., keine mit "Selected="no"" markierten Elemente einzuschließen. Allerdings müssen alle Elemente mit "Selected="yes"" weiterhin am Ende der Datei "AdminDeployment.xml" platziert werden.

> [!IMPORTANT]
>  Während der Installation startet der Computer möglicherweise mehrere Male erneut. Nach dem Neustart müssen Sie zum Ausführen der Installation sich wieder mit demselben Benutzerkonto anmelden, mit dem Sie angemeldet waren, bevor der Computer neu gestartet wurde. Automatische Neustarts können vermieden werden, indem die erforderlichen Komponenten vor dem Ausführen einer unbeaufsichtigten Installation vorinstalliert werden. Weitere Informationen finden Sie im Abschnitt: "Vermeiden eines Neustarts während des Setups" im [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

 Das AdminDeployment-Dateischema enthält die folgenden Elemente:

|Element|Attribut|Werte|Beschreibung|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Pfad*|Identisches Verhalten wie beim Überschreiben eines Pfades in der Benutzeroberfläche der Installationsanwendung. Dieses Element wird ignoriert, wenn Visual Studio bereits installiert ist.|
|BundleCustomizations|NoWeb|Ja&#124;Standard|Wenn der Wert dieses Elements "Ja" lautet, versucht die Installationsanwendung nie, während der Setupaktion ins Internet zu wechseln.|
|SelectableItemCustomization|Hidden|Ja&#124;Nein|Wenn der Wert dieses Elements "Ja" lautet, wird ein wählbares Element in der Anpassungsstruktur ausgeblendet.|
|SelectableItemCustomization|Ausgewählt|Ja&#124;Nein|Wählt ein wählbares Element in der Anpassungsstruktur aus oder löscht dieses.|
|BundleCustomizations|Feed|Pfad|Speicherort des Feeds, den der Benutzer verwenden möchte.  Dieser Feed wird für nachfolgende Änderungsvorgänge auf dem Computer verwendet (standardmäßig "Default").|
|BundleCustomizations|SuppressRefreshPrompt|Ja&#124;Standard|Verhindert, dass der Benutzer aufgefordert wird, das Setup zu aktualisieren, wenn eine neuere Version verfügbar ist.|
|BundleCustomizations|NoRefresh|Ja&#124;Standard|Das Setup wird nicht aktualisiert, wenn eine neuere Version verfügbar ist.|
|BundleCustomizations|NoCacheOnlyMode|Ja&#124;Standard|Verhindert, dass der Paket-Cache vorab gefüllt wird.|

> [!WARNING]
>  Die Installationsanwendung berücksichtigt den Auswahlzustand eines auswählbaren Elements, selbst wenn es ausgeblendet ist. Wenn Sie beispielsweise ein wählbares Element immer installieren möchten, können Sie es als ausgeblendet und ausgewählt markieren.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Erstellen einer unbeaufsichtigten Installation von Visual Studio

1.  Ändern Sie in der Datei „ *Laufwerk*:\IDEinstall\AdminDeployment.xml“ den Wert des „NoWeb“-Attributs des „BundleCustomizations“-Elements von „default“ in „yes“, wie im folgenden Beispiel gezeigt:

     Ändern Sie `<BundleCustomizations TargetDir="default" NoWeb="default"/>` in `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2.  Ändern Sie das SelectableItemCustomizations-Attribut ggf. für optionale Komponenten, und speichern Sie die Datei.

## <a name="running-unattended-setup"></a>Ausführen der unbeaufsichtigten Installation
 Sie können eine unbeaufsichtigte Installation ausführen, indem Sie die Installationsanwendung für Visual Studio entweder automatisch auf Clientcomputern ausführen oder indem Sie zulassen, dass Benutzer die Anwendung selbst mit Einstellungen auszuführen, die Sie definieren.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Ausführen einer unbeaufsichtigten Installation auf einem Clientcomputer

- Öffnen der **starten** Menü wählen **ausführen**, und geben Sie dann \\ \\ *ServerName*\IDEinstall\vs_*Produkt*.exe "/ adminfile" *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>

   Beispielsweise können Sie die folgende Befehlszeile angeben: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Aktivieren von Clients, um Visual Studio mit vordefinierten Einstellungen manuell zu installieren

1.  Kopieren Sie die benutzerdefinierte Datei „AdminDeployment.xml“ in eine schreibgeschützte Netzwerkfreigabe (beispielsweise „\\\\*ServerName*\IDEinstall\packages\AdminDeployment.xml“).

2.  Aktivieren Sie Benutzer für die Installation von dieser Freigabe.

## <a name="maintaining-an-installation"></a>Verwalten einer Installation
 Wenn Sie **Systemsteuerung** öffnen und die Installationsanwendung erneut ausführen, können Sie Funktionen von Visual Studio ändern, Programmiersprachen deinstallieren und Visual Studio reparieren bzw. deinstallieren.

> [!NOTE]
>  Sie müssen über Administratoranmeldeinformationen auf dem lokalen Computer verfügen, um den Wartungsmodus zu verwenden.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Verwalten einer Installation auf einem Clientcomputer

-   Öffnen Sie **Systemsteuerung**, und wählen Sie dann **Programme und Funktionen**aus.

-   Wählen Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]und dann **Ändern**aus.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Ändern der AdminDeployment-Einstellungen auf einem Clientcomputer nach der Installation von Visual Studio

1. Aktualisieren Sie ggf. "AdminDeployment.xml".

2. Öffnen Sie das Menü **Start** , und wählen Sie dann **Ausführen**aus.

3. Geben Sie folgenden Text ein: \\\\*ServerName*\IDEinstall\vs_*Produkt*.exe "/ adminfile" PathToAdmindeployment.xml-Datei

    AdditionalParametersAsNeeded

    Beispielsweise können Sie die folgende Befehlszeile angeben: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   "Reparieren" ist der Standardparameter nach der Installation von Visual Studio. Wenn Sie Visual Studio mit aktualisierter/adminfile reparieren, überschreiben Sie die aktuellen Einstellungen der Admin-Bereitstellung mit denjenigen, die die aktualisierte AdminDeployment.xml-Datei aufruft.

## <a name="updating-an-installation"></a>Aktualisieren einer installation
 Microsoft hat einige Updates für Visual Studio 2015 veröffentlicht. In diesem Abschnitt wird erläutert, wie Sie Ihr Image für die unbeaufsichtigte Installation von Visual Studio 2015 aktualisieren, sodass sie die Updates enthält.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Um eine unbeaufsichtigte Installation von Visual Studio zu aktualisieren.

1. Suchen Sie die Product.exe-Datei in das bestehende Netzwerkimage um, mit der rechten Maustaste sie und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf die **Details** Registerkarte, und notieren Sie sich die **Produktversion** Eigenschaft.

    ![Beispiel für das Dialogfeld "Eigenschaften" in einer unbeaufsichtigten Installation von Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "für die unbeaufsichtigte Installation - Dialogfeld")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Wenn die Produktversion 14.0.24720.0 oder 14.0.24720.1 ist, gehen Sie wie folgt vor:
4. 1.  Führen Sie *Product.exe* /Layout *Laufwerk:* \IDEinstall auf einem Computer, der Zugang zum Internet hat. (Führen Sie zum Beispiel `vs_enterprise.exe /Layout d:\IDEinstall` aus.)

   2.  Nachdem die/Layout abgeschlossen ist, kopieren Sie das neue Image an einem neuen Speicherort.

   3.  Erstellen Sie und ändern Sie die Datei "admindeployment.xml". Verwenden Sie hierzu die `/CreateAdminFile`  *\<Dateispeicherort >* Befehlszeilenparameter. (Weitere Informationen finden Sie im Abschnitt "Bereitstellen von Visual Studio im unbeaufsichtigten Modus" in diesem Artikel.)

   4.  Führen Sie auf dem Clientcomputer, den folgenden Befehl aus, um die Kopie von Visual Studio zu aktualisieren, die Sie zuvor installiert: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe*  "/ adminfile" \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart ".

        Führen Sie zum Beispiel `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart` aus.
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Gehen Sie für andere produktversionswerte folgendermaßen vor:
6. 1.  Führen Sie *Product.exe* /Layout *Laufwerk:* \IDEinstall auf einem Computer, der Zugang zum Internet hat. (Führen Sie zum Beispiel `vs-enterprise.exe /Layout d:\IDEinstall` aus.)

   2.  Nachdem die/Layout abgeschlossen ist, kopieren Sie das neue Image an einem neuen Speicherort. (Oder Sie können stattdessen das bestehende Netzwerkimage um überschreiben.)

   3.  Erstellen Sie und ändern Sie die Datei "admindeployment.xml". Verwenden Sie hierzu die `/CreateAdminFile`  *\<Dateispeicherort >* Befehlszeilenparameter. (Weitere Informationen finden Sie im Abschnitt "Bereitstellen von Visual Studio im unbeaufsichtigten Modus" in diesem Artikel.)

   4.  Wenn Sie das Bild in einem neuen Speicherort kopieren, müssen Sie den folgenden Befehl ausführen, auf dem Clientcomputer, die Kopie von Visual Studio zu aktualisieren, die Sie zuvor installiert haben: "\\\\*server1*\IDEinstall_Updated_1\\ *Product.exe* "/ adminfile" \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart ".

        Führen Sie zum Beispiel `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart` aus.

   5.  Wenn Sie das bestehende Netzwerkimage um überschreiben, können können Sie den Befehl ausführen, wie im vorherigen Schritt aufgeführt, oder Sie Folgendes:

   6.  1.  Öffnen Sie **Systemsteuerung**, und wählen Sie dann **Programme und Funktionen**aus.

       2.  Wählen Sie **Visual Studio**, und wählen Sie dann **Änderung**.

       3.  Nach dem Start von Visual Studio im Wartungsmodus befindet, klicken Sie auf **ändern**.

       4.  Das neueste Update sollte auf der Seite "Features" angezeigt werden. Wählen Sie die anderen Funktionen, die Sie installieren möchten, klicken Sie auf **Weiter**, und klicken Sie dann auf **aktualisieren** sowohl für das Update als auch für die neuen Features zu installieren.

## <a name="registering-the-product"></a>Das Produkt registrieren
 Nachdem die Installation abgeschlossen ist, können Sie Ihre Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aus [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]heraus registrieren.

#### <a name="to-register"></a>Zum Registrieren führen Sie Folgendes aus:

1.  Öffnen Sie das Menü **Hilfe** , und wählen Sie dann die Option **Produkt registrieren**aus.

2.  Geben Sie den Product Key ein.

     (Weitere Informationen finden Sie unter den [Vorgehensweise: Suchen des Visual Studio Product Key](../install/how-to-locate-the-visual-studio-product-key.md) und [Vorgehensweise: Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) Themen.)

## <a name="see-also"></a>Siehe auch
 [Installieren von Visual Studio](../install/install-visual-studio-2015.md)