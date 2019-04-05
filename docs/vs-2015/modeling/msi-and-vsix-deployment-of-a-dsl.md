---
title: MSI- und VSIX-Bereitstellung einer DSL | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bf826a45fbb7f5fc23ffad36dc2adba0442cd3a1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958050"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>MSI- und VSIX-Bereitstellung einer DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine domänenspezifische Sprache auf Ihrem eigenen Computer oder auf anderen Computern installieren. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] muss bereits auf dem Zielcomputer installiert sein.  
  
##  <a name="which"></a> Auswählen zwischen VSIX-als auch MSI-Bereitstellung  
 Es gibt zwei Methoden zum Bereitstellen einer domänenspezifischen Sprache:  
  
|Methode|Vorteile|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterung)|Sehr leicht bereitzustellen: Kopieren Sie aus, und führen Sie die **VSIX** Datei aus dem DslPackage-Projekt.<br /><br /> Weitere Informationen finden Sie unter [installieren und Deinstallieren eine DSL mithilfe der VSX](#Installing).|  
|MSI-Datei (Installationsdatei)|– Ermöglicht es dem Benutzer zum Öffnen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] durch Doppelklicken auf eine DSL-Datei.<br />: Ordnet ein Symbol mit dem Typ des DSL-Datei auf dem Zielcomputer an.<br />: Ordnet ein XSD-Schema (XML-Schema) mit dem DSL-Dateityp an. Dadurch werden Warnungen vermieden, wenn in die Datei geladen werden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].<br /><br /> Sie müssen ein Setup-Projekt zu Ihrer Lösung erstellen Sie eine MSI-Datei hinzufügen.<br /><br /> Weitere Informationen finden Sie unter [mithilfe einer MSI-Datei für die Bereitstellung einer DSL](#msi).|  
  
##  <a name="Installing"></a> Installieren und Deinstallieren eine DSL mithilfe der VSX  
 Wenn Ihre DSL, die von dieser Methode installiert wird, kann der Benutzer innerhalb eine DSL-Datei öffnen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aber die Datei kann nicht aus dem Windows-Explorer nicht geöffnet werden.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>So installieren Sie eine DSL mithilfe der VSX  
  
1.  Suchen Sie Ihre Computer nach der **VSIX** -Datei, die vom Projekt DSL-Paket erstellt wurde.  
  
    1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **DslPackage** Projekt, und klicken Sie dann auf **Ordner in Windows Explorer öffnen**.  
  
    2.  Suchen Sie die Datei **Bin\\\*\\**_IhrProjekt_**. DslPackage.vsix**  
  
2.  Kopieren der **VSIX** Datei auf den Zielcomputer, auf dem Sie die DSL installieren möchten. Dies kann Ihr eigener Computer oder ein anderer Computer sein.  
  
    -   Der Zielcomputer müssen eine der Editionen von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , die DSLs zur Laufzeit unterstützt. Weitere Informationen finden Sie unter [unterstützt Visual Studio-Editionen für das Visualisierungs- und Modellierungs-SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   Der Zielcomputer müssen eine der Editionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im angegebenen **DslPackage\source.extensions.manifest**.  
  
3.  Doppelklicken Sie auf dem Zielcomputer auf die **VSIX** Datei.  
  
     **Installer für Visual Studio-Erweiterungen** wird geöffnet, und die Erweiterung wird installiert.  
  
4.  Starten Sie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], bzw. starten Sie die Anwendung neu.  
  
5.  Verwenden Sie zum Testen der DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zum Erstellen einer neuen Datei mit der Dateierweiterung an, die Sie für Ihre DSL definiert.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>So deinstallieren Sie eine DSL, die sich mit VSX installiert wurde  
  
1. Auf der **Tools** Menü klicken Sie auf **Erweiterungs-Manager**.  
  
2. Erweitern Sie **Installierte Erweiterungen**.  
  
3. Wählen Sie die Erweiterung in der DSL definiert ist, und klicken Sie dann auf **Deinstallieren**.  
  
   In seltenen Fällen kann es vorkommen, dass eine fehlerhafte Erweiterung nicht geladen und ein Bericht im Fehlerfenster erstellt wird, aber im Erweiterungs-Manager keine Informationen angezeigt werden. Sie haben die Möglichkeit, die Erweiterung zu entfernen, indem Sie die Datei aus dem folgenden Ordner löschen:  
  
   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="msi"></a> Bereitstellung einer DSL in eine MSI-Datei  
 Definieren Sie eine MSI-Datei (Windows Installer)-Datei für Ihre DSL, können Sie Benutzern das Öffnen von DSL-Dateien aus dem Windows-Explorer von erlauben. Sie können auch ein Symbol und eine kurze Beschreibung Ihrer Dateinamenerweiterung zuordnen. Darüber hinaus kann die MSI-Datei ein XSD-Schema installieren, die zum Überprüfen der DSL-Dateien verwendet werden kann. Wenn Sie möchten, können Sie andere Komponenten in die MSI-Datei hinzufügen, die zur selben Zeit installiert werden.  
  
 Weitere Informationen zu MSI-Dateien und andere Bereitstellungsoptionen finden Sie unter [Bereitstellen von Anwendungen, Dienste und Komponenten](../deployment/deploying-applications-services-and-components.md).  
  
 Um eine MSI-Datei zu erstellen, die Sie Hinzufügen eines Setup-Projekts zu Ihrer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Lösung. Die einfachste Methode zum Erstellen eines Setupprojekts ist die Verwendung die Vorlage CreateMsiSetupProject.tt, das Sie herunterladen können die [VMSDK-Website](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Bereitstellen eine DSL in eine MSI-Datei  
  
1. Legen Sie `InstalledByMsi` im Erweiterungsmanifest. Dadurch wird verhindert, dass die VSX installiert und mit Ausnahme von der MSI-Datei deinstalliert werden. Dies ist wichtig, wenn Sie andere Komponenten in die MSI-Datei aufnehmen werden.  
  
   1.  Öffnen Sie DslPackage\source.extension.tt  
  
   2.  Fügen Sie die folgende Zeile vor `<SupportedProducts>`:  
  
       ```  
       <InstalledByMsi>true</InstalledByMsi>  
       ```  
  
2. Erstellen Sie oder bearbeiten Sie ein Symbol, das Ihre DSL im Windows-Explorer dargestellt wird. Bearbeiten Sie z. B. **DslPackage\Resources\File.ico**  
  
3. Stellen Sie sicher, dass die folgenden Attribute Ihrer DSL korrekt sind:  
  
   -   Klicken Sie im DSL-Explorer klicken Sie auf den Stammknoten, und überprüfen Sie im Fenster "Eigenschaften":  
  
       -   Beschreibung  
  
       -   Version  
  
   -   Klicken Sie auf die **Editor** Knoten, und klicken Sie im Fenster Eigenschaften auf **Symbol**. Legen Sie den Wert auf eine Symboldatei in **DslPackage\Resources**, z. B. **File.ico**  
  
   -   Auf der **erstellen** öffnen **Configuration Manager**, und wählen Sie die Konfiguration, die Sie erstellen wie z. B., möchten **Version** oder **Debuggen** .  
  
4. Wechseln Sie zu [Visualisierungs- und Modellierungs-SDK auf der Startseite](http://go.microsoft.com/fwlink/?LinkID=186128), und von der **Downloads** Registerkarte, zum Downloadpfad **CreateMsiSetupProject.tt**.  
  
5. Hinzufügen **CreateMsiSetupProject.tt** zu Ihrem Dsl-Projekt.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt eine Datei mit dem Namen **CreateMsiSetupProject.vdproj**.  
  
6. Kopieren Sie im Windows-Explorer Dsl\\\*.vdproj in einen neuen Ordner mit dem Namen Setup.  
  
    (Wenn Sie möchten, können Sie jetzt CreateMsiSetupProject.tt aus Ihrem Dsl-Projekt ausschließen.)  
  
7. In **Projektmappen-Explorer**, fügen **Setup\\\*.vdproj** wie ein vorhandenes Projekt.  
  
8. Auf der **Projekt** Menü klicken Sie auf **Projektabhängigkeiten**.  
  
    In der **Projektabhängigkeiten** Dialogfeld Feld, wählen Sie das Setupprojekt.  
  
    Aktivieren Sie das Kontrollkästchen neben **DslPackage**.  
  
9. Generieren Sie die Projektmappe neu.  
  
10. Suchen Sie im Windows-Explorer die erstellte MSI-Datei im Setup-Projekt ein.  
  
     Kopieren Sie die MSI-Datei auf einem Computer, auf dem Sie Ihre DSL installieren möchten. Doppelklicken Sie auf die MSI-Datei. Das Installationsprogramm ausgeführt wird.  
  
11. Erstellen Sie eine neue Datei mit der Erweiterung Ihrer DSL, auf dem Zielcomputer. Überprüfen Sie Folgendes:  
  
    -   In Windows Explorer-Listenansicht wird die Datei angezeigt, mit dem Symbol und eine Beschreibung ein, die Sie definiert.  
  
    -   Wenn Sie die Datei doppelklicken, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] beginnt, und die DSL-Datei in Ihrem DSL-Editor geöffnet.  
  
    Falls gewünscht, können Sie das Setup-Projekt manuell erstellen, anstatt die Textvorlage. Eine exemplarische Vorgehensweise, die diese Prozedur umfasst finden Sie in Kapitel 5 des der [Visualisierungs- und Modellierungs-SDK-Lab](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>So deinstallieren Sie eine DSL, die über eine MSI-Datei installiert wurde  
  
1.  Öffnen Sie in Windows, die **Programme und Funktionen** Systemsteuerung.  
  
2.  Deinstallieren Sie die DSL ein.  
  
3.  Starten Sie Visual Studio neu.
