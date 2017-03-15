---
title: "MSI- und VSIX-Bereitstellung einer DSL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 2
---
# MSI- und VSIX-Bereitstellung einer DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine domänenspezifische Sprache auf Computer besitzen oder auf anderen Computern installieren.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muss auf dem Zielcomputer bereits installiert sind.  
  
##  <a name="which"></a> Zwischen VSIX\- und MSI\-Bereitstellung auswählen  
 Es gibt zwei Arten der Bereitstellung einer domänenspezifischen Sprache:  
  
|Methode|Vorteile|  
|-------------|--------------|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(VSX Erweiterung\)|Sehr einfach bereitzustellen: Kopieren Sie **.vsix** und führen Sie die Datei vom DslPackage\-Projekt aus.<br /><br /> Weitere Informationen finden Sie unter [Ein DSL mit dem VSX Installieren und Deinstallieren](#Installing).|  
|Installationsprogrammdatei \(MSI\)|-   Ermöglicht es dem Benutzer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] durch Doppelklicken auf eine DSL\-Datei zu öffnen.<br />-   Ordnet ein Symbol mit dem DSL\-Dateityp in dem Zielcomputer.<br />-   Ordnet ein XML\-Schema \(XSD\) mit dem DSL\-Dateityp.  Dies vermeidet Warnungen, wenn die Datei in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]geladen wird.<br /><br /> Sie müssen ein Setup\-Projekt hinzufügen, um ein MSI der Projektmappe zu erstellen.<br /><br /> Weitere Informationen finden Sie unter [Ein DSL mit einer MSI\-Datei bereitstellen](#msi).|  
  
##  <a name="Installing"></a> Ein DSL mit dem VSX Installieren und Deinstallieren  
 Wenn das DSL so installiert ist, kann der Benutzer eine DSL\-Datei aus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]öffnen, aber die Datei aus Windows Explorer kann nicht geöffnet werden.  
  
#### So fügen Sie ein DSL mit dem VSX installieren  
  
1.  Im Computer suchen Sie die Datei, die von **.vsix** DSL\-Paket das Projekt erstellt wurde.  
  
    1.  In **Projektmappen\-ExplorerDslPackage** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Ordner in Windows Explorer öffnen**.  
  
    2.  Suchen Sie nach der Datei **bin\\\*\\***IhrProjekt***.DslPackage.vsix**.  
  
2.  Kopieren Sie die Datei **.vsix** auf den Zielcomputer, auf dem das DSL installieren möchten.  Dies kann Ihr eigener Computer oder ein anderer Computer sein.  
  
    -   Der Zielcomputer muss eine der Editionen von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] DSL verfügen, die zur Laufzeit unterstützt.  Weitere Informationen finden Sie unter [Visual Studio\-Editionen unterstützt für Visualisierung und Modellierung SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   Der Zielcomputer muss eine der Editionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in **DslPackage\\source.extensions.manifest**angegeben haben.  
  
3.  Doppelklicken Sie auf dem Zielcomputer auf die **.vsix**\-Datei.  
  
     **Installer für Visual Studio\-Erweiterungen** wird geöffnet, und die Erweiterung wird installiert.  
  
4.  Starten Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], bzw. starten Sie die Anwendung neu.  
  
5.  So testen Sie das DSL, verwenden Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , eine neue Datei zu erstellen, die die Erweiterung enthält, die Sie für das DSL definiert haben.  
  
#### So fügen Sie ein DSL deinstallieren, das installiert wurde, indem Sie die VSX  
  
1.  Klicken Sie im Menü **Extras** auf **Erweiterungs\-Manager**.  
  
2.  Erweitern Sie **Installierte Erweiterungen**.  
  
3.  Wählen Sie die Erweiterung, in der das DSL definiert ist, und klicken Sie dann auf **Deinstallieren**.  
  
 In seltenen Fällen kann es vorkommen, dass eine fehlerhafte Erweiterung nicht geladen und ein Bericht im Fehlerfenster erstellt wird, aber im Erweiterungs\-Manager keine Informationen angezeigt werden.  Sie haben die Möglichkeit, die Erweiterung zu entfernen, indem Sie die Datei aus dem folgenden Ordner löschen:  
  
 *LocalAppData* **\\Microsoft\\VisualStudio\\10.0\\Extensions**  
  
##  <a name="msi"></a> Ein DSL in einem MSI bereitstellen  
 Indem Sie eine Windows Installer \(MSI\) \- Datei für das DSL definieren, können Sie Benutzern ermöglichen, DSL\-Dateien von Windows Explorer zu öffnen.  Sie können ein Symbol und eine kurze Beschreibung mit der Dateinamenerweiterung auch zuordnen.  Darüber hinaus kann die MSI\-Datei eine XSD installieren, die verwendet werden kann, um DSL\-Dateien zu überprüfen.  Bei Bedarf können Sie weitere Komponenten in die MSI\-Datei hinzufügen, das zur selben Zeit installiert wird.  
  
 Weitere Informationen über MSI\-Dateien und weitere Bereitstellungsoptionen finden Sie unter [Bereitstellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md).  
  
 Um eine MSI\-Datei zu erstellen, fügen Sie ein Setup\-Projekt der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektmappe hinzu.  Die einfachste Möglichkeit zum Erstellen eines Setup\-Projekts ist, die CreateMsiSetupProject.tt\-Vorlage zu verwenden, die Sie herunterladen können. [VMSDK site](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
#### So fügen Sie ein DSL in einem MSI bereitstellen  
  
1.  Legen Sie `InstalledByMsi` in manifest Erweiterung fest.  Dadurch wird verhindert, dass das VSX außer durch die MSI\-Datei installiert und deinstalliert.  Dies ist wichtig, wenn Sie andere Komponenten im MSI einschließen.  
  
    1.  Öffnen Sie DslPackage \\ source.extension.tt  
  
    2.  Fügen Sie die folgende Zeile vor `<SupportedProducts>`ein:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  Erstellen oder bearbeiten Sie ein Symbol, das das DSL in Windows Explorer darstellt.  Bearbeiten Sie beispielsweise **DslPackage\\Resources\\File.ico**  
  
3.  Überprüfen Sie, ob die folgenden Attribute des DSL richtig sind:  
  
    -   In DSL\-Explorer klicken Sie auf den Stammknoten aus, und legen Sie im Eigenschaftenfenster die Überprüfung:  
  
        -   Beschreibung  
  
        -   Version  
  
    -   Klicken Sie auf den Knoten **Editor** , und legen Sie im Eigenschaftenfenster auf **Symbol**.  Legen Sie den Wert fest, um eine Symboldatei in **DslPackage\\Resources**zu verweisen, wie **File.ico**  
  
    -   Zeigen Sie im Menü **Erstellen** Öffnen **Konfigurations\-Manager**und die Konfiguration, die Sie erstellen möchten, wie **Release** oder **Debuggen**aus.  
  
4.  [Visualization and Modeling SDK home page](http://go.microsoft.com/fwlink/?LinkID=186128)Und aus der Registerkarte **Downloads** , Download **CreateMsiSetupProject.tt**.  
  
5.  Fügen Sie dem Dsl\-Projekt **CreateMsiSetupProject.tt** hinzu.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt eine Datei mit dem Namen **CreateMsiSetupProject.vdproj**.  
  
6.  In Windows\-Explorer benannte Kopie Dsl an \*.vdproj \\ Setup einen neuen Ordner.  
  
     \(Wenn Sie möchten, können Sie jetzt Dsl\-Projekt vom CreateMsiSetupProject.tt ausschließen.\)  
  
7.  In **Projektmappen\-Explorer**fügen Sie **Setup\\\*.vdproj** als vorhandenes Projekt hinzu.  
  
8.  Klicken Sie im Menü **Projekt** auf **Projektabhängigkeiten**.  
  
     Wählen Sie im Dialogfeld **Projektabhängigkeiten** das Setup\-Projekt aus.  
  
     Aktivieren Sie das Kontrollkästchen neben **DslPackage**aus.  
  
9. Generieren Sie die Projektmappe neu.  
  
10. Suchen Sie in Windows Explorer die erstellte MSI\-Datei im Setup\-Projekt.  
  
     Kopieren Sie die MSI\-Datei auf einem Computer, auf dem das DSL installieren möchten.  Doppelklicken Sie auf die MSI\-Datei.  Das Installationsprogramm wird ausgeführt.  
  
11. Im Zielcomputer erstellen Sie eine neue Datei mit der Dateierweiterung des DSL verfügt.  Überprüfen Sie die:  
  
    -   In Windows\-Explorer\-Listenansicht scheint die Datei mit dem Symbol und Beschreibung, die Sie definiert haben.  
  
    -   Wenn Sie auf die Datei doppelklicken, öffnet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und beginnt die DSL\-Datei im DSL\-Editor.  
  
 Wenn Sie es vorziehen, können Sie das Setup\-Projekt manuell erstellen, anstatt die Textvorlage zu verwenden.  Eine exemplarische Vorgehensweise, die diese Prozedur umfasst finden Sie in Kapitel 5 aus [Visualization and Modeling SDK Lab](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### So fügen Sie ein DSL deinstallieren, das von einem MSI\-Datei installiert wurde  
  
1.  Unter Windows **Programme und Funktionen** Öffnen Sie die Systemsteuerung.  
  
2.  Deinstallieren Sie das DSL.  
  
3.  Starten Sie Visual Studio neu.