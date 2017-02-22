---
title: "Deploying COM Components with ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "registration-free COM deployment"
  - "ClickOnce deployment, COM components"
  - "COM components, deploying"
  - "deploying applications [ClickOnce], COM components"
  - "components, deploying"
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Deploying COM Components with ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Bereitstellung von älteren COM\-Komponenten war schon immer eine anspruchsvolle Aufgabe.  Die Komponenten müssen global registriert sein und können daher unerwünschte negative Auswirkungen auf Anwendungen mit gemeinsamen Adressbereichen haben.  Diese Situation stellt in .NET Framework\-Anwendungen im Allgemeinen kein Problem dar, da Komponenten für eine Anwendung vollständig isoliert oder parallel kompatibel sind.  Mit Visual Studio können isolierte COM\-Komponenten unter Windows XP oder neueren Betriebssystemen bereitgestellt werden.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bietet eine einfache und sichere Methode zum Bereitstellen von .NET\-Anwendungen.  Wenn Ihre Anwendungen jedoch ältere COM\-Komponenten verwenden, sind für die Bereitstellung weitere Schritte erforderlich.  In diesem Thema wird das Bereitstellen isolierter COM\-Komponenten und das Verweisen auf systemeigene Komponenten \(z. B. von Visual Basic 6.0 oder Visual C\+\+\) beschrieben.  
  
 Weitere Informationen zum Bereitstellen isolierter COM\-Komponenten finden Sie unter "Simplify App Deployment with [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] and Registration\-Free COM" unter [http:\/\/msdn.microsoft.com\/de\-de\/magazine\/default.aspx](http://msdn.microsoft.com/de-de/magazine/default.aspx).  
  
## COM ohne Registrierung  
 Das COM ohne Registrierung stellt eine neue Technologie zum Bereitstellen und Aktivieren isolierter COM\-Komponenten dar.  Dabei werden alle i. d. R. in der Systemregistrierung installierten Typbibliothek\- und Registrierungsinformationen der Komponente in einer XML\-Datei abgelegt, die als Manifest bezeichnet wird und in demselben Ordner wie die Anwendung gespeichert ist.  
  
 Um eine COM\-Komponente zu isolieren, muss diese auf dem Computer des Entwicklers registriert sein, nicht jedoch auf dem Computer des Endbenutzers.  Zum Isolieren einer COM\-Komponente müssen Sie nur die **Isolated**\-Eigenschaft ihres Verweises auf **True** festlegen.  Standardmäßig ist diese Eigenschaft auf **False** festgelegt, wodurch angegeben wird, dass sie als registrierter COM\-Verweis behandelt werden soll.  Wenn diese Eigenschaft **True** ist, wird für die Komponente bei der Erstellung ein Manifest generiert.  Außerdem werden dadurch während der Installation die entsprechenden Dateien in den Anwendungsordner kopiert.  
  
 Wenn der Manifestgenerator auf einen isolierten COM\-Verweis trifft, listet er alle `CoClass`\-Einträge in der Typbibliothek der Komponente auf, gleicht alle Einträge mit den jeweiligen Registrierungsdaten ab und generiert für alle COM\-Klassen in der Typbibliothekdatei Manifestdefinitionen.  
  
## Bereitstellen von COM\-Komponenten ohne Registrierung mit ClickOnce  
 Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungstechnologie eignet sich gut zum Bereitstellen isolierter COM\-Komponenten, da sowohl [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] als auch das COM ohne Registrierung erfordern, dass eine Komponente zum Bereitstellen über ein Manifest verfügt.  
  
 In der Regel stellt der Autor der Komponente das Manifest zur Verfügung.  Wenn dies nicht der Fall ist, kann von Visual Studio automatisch ein Manifest für eine COM\-Komponente generiert werden.  Das Generieren eines Manifests wird während des [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Veröffentlichungsprozesses ausgeführt. Weitere Informationen finden Sie unter [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md).  Durch dieses Feature können auch ältere Komponenten weiterverwendet werden, die mit früheren Entwicklungsumgebungen wie Visual Basic 6.0 erstellt wurden.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] stellt COM\-Komponenten auf zweierlei Arten bereit:  
  
-   Verwenden Sie den Bootstrapper, um die COM\-Komponenten bereitzustellen. Dies funktioniert auf allen unterstützten Plattformen.  
  
-   Verwenden Sie die systemeigene Bereitstellung isolierter Komponenten \(auch bekannt als COM ohne Registrierung\).  Dies funktioniert jedoch nur unter Windows XP oder einem höheren Betriebssystem.  
  
### Beispiel für das Isolieren und Bereitstellen einer einfachen COM\-Komponente  
 Zur Veranschaulichung der Bereitstellung von COM\-Komponenten ohne Registrierung wird in diesem Beispiel eine Windows\-basierte Anwendung in Visual Basic erstellt, die auf eine mit Visual Basic 6.0 erstellte isolierte systemeigene COM\-Komponente verweist und diese mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitstellt.  
  
 Zuerst müssen Sie die systemeigene COM\-Komponente erstellen:  
  
##### So erstellen Sie eine systemeigene COM\-Komponente  
  
1.  Klicken Sie in Visual Basic 6.0 im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** den **Visual Basic**\-Knoten aus, und wählen Sie ein **ActiveX\-DLL**\-Projekt aus.  Geben Sie im Feld **Name** den Text `VB6Hello` ein.  
  
    > [!NOTE]
    >  Das COM ohne Registrierung unterstützt nur ActiveX\-DLL\- und ActiveX\-Steuerelement\-Projekttypen; ActiveX\-EXE\- und ActiveX\-Dokumentprojekttypen werden nicht unterstützt.  
  
3.  Doppelklicken Sie im **Projektmappen\-Explorer** auf **Class1.vb**, um den Text\-Editor zu öffnen.  
  
4.  Fügen Sie in Class1.vb nach dem generierten Code für die `New`\-Methode den folgenden Code hinzu:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Erstellen Sie die Komponente.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
> [!NOTE]
>  Das COM ohne Registrierung unterstützt nur DLLs und COM\-Steuerelement\-Projekttypen.  EXE\-Dateien können mit dem COM ohne Registrierung nicht verwendet werden.  
  
 Sie können nun eine Windows\-basierte Anwendung erstellen und dieser einen Verweis auf die COM\-Komponente hinzufügen.  
  
##### So erstellen Sie mit einer COM\-Komponente eine Windows\-basierte Anwendung  
  
1.  Klicken Sie in Visual Basic im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** den **Visual Basic**\-Knoten aus, und wählen Sie **Windows\-Anwendung** aus.  Geben Sie im Feld **Name** die Zeichenfolge `RegFreeComDemo` ein.  
  
3.  Klicken Sie im **Projektmappen\-Explorer** auf die Schaltfläche **Alle Dateien anzeigen**, um die Projektverweise anzuzeigen.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Knoten **Verweise**, und wählen Sie im Kontextmenü die Option **Verweis hinzufügen** aus.  
  
5.  Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Durchsuchen**, navigieren Sie zu VB6Hello.dll, und wählen Sie die Datei aus.  
  
     In der Verweisliste wird ein **VB6Hello**\-Verweis angezeigt.  
  
6.  Zeigen Sie auf die **Toolbox**, wählen Sie ein **Button**\-Steuerelement aus, und ziehen Sie es in das Formular **Form1**.  
  
7.  Legen Sie im **Eigenschaftenfenster** die **Text**\-Eigenschaft der Schaltfläche auf "Hello" fest.  
  
8.  Doppelklicken Sie auf die Schaltfläche, um Handlercode hinzuzufügen, und fügen Sie in der Codedatei Code hinzu, sodass der Handler folgendermaßen aussieht:  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Führen Sie die Anwendung aus.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
 Isolieren Sie danach das Steuerelement.  Jede von der Anwendung verwendete COM\-Komponente wird im Projekt als COM\-Verweis dargestellt.  Diese Verweise werden im Fenster **Projektmappen\-Explorer** unter dem Knoten **Verweise** angezeigt.  \(Beachten Sie, dass Sie Verweise entweder direkt mit dem Befehl **Verweis hinzufügen** im Menü **Projekt** oder indirekt durch Ziehen eines ActiveX\-Steuerelements in das Formular hinzufügen können.\)  
  
 In den folgenden Schritten wird das Isolieren der COM\-Komponente und das Veröffentlichen der aktualisierten Komponente dargestellt, die das isolierte Steuerelement enthält:  
  
##### So isolieren Sie eine COM\-Komponente  
  
1.  Wählen Sie im **Projektmappen\-Explorer** im Knoten **Verweise** den **VB6Hello**\-Verweis aus.  
  
2.  Ändern Sie im **Eigenschaftenfenster** den Wert der **Isolated**\-Eigenschaft von **False** auf **True**.  
  
3.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
 Wenn Sie nun F5 drücken, wird die Anwendung wie erwartet, jedoch unter einem COM ohne Registrierung ausgeführt.  Um dies zu überprüfen, versuchen Sie, die Registrierung der Komponente VB6Hello.dll rückgängig zu machen und RegFreeComDemo1.exe außerhalb der Visual Studio\-IDE auszuführen.  Wenn Sie jetzt die Taste drücken, wird die Anwendung immer noch ausgeführt.  Wenn Sie das Anwendungsmanifest vorübergehend umbenennen, schlägt die Ausführung wieder fehl.  
  
> [!NOTE]
>  Sie können das Fehlen einer COM\-Komponente simulieren, indem Sie vorübergehend deren Registrierung aufheben.  Öffnen Sie eine Eingabeaufforderung, wechseln Sie zum Systemordner, indem Sie `cd /d %windir%\system32` eingeben, und heben Sie die Registrierung mit dem Befehl `regsvr32 /u VB6Hello.dll` auf.  Sie können die Komponente mit dem Befehl `regsvr32 VB6Hello.dll` erneut registrieren.  
  
 Der abschließende Schritt besteht darin, die Anwendung mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zu veröffentlichen:  
  
##### So veröffentlichen Sie ein Anwendungsupdate mit einer isolierten COM\-Komponente  
  
1.  Klicken Sie im Menü **Erstellen** auf **RegFreeComDemo veröffentlichen**.  
  
     Der Webpublishing\-Assistent wird angezeigt.  
  
2.  Geben Sie im Webpublishing\-Assistenten einen Speicherort auf dem Datenträger des lokalen Computers an, an dem Sie auf die veröffentlichten Dateien zugreifen und diese untersuchen können.  
  
3.  Klicken Sie auf **Fertig stellen**, um die Anwendung zu veröffentlichen.  
  
 Wenn Sie die veröffentlichten Dateien untersuchen, werden Sie bemerken, dass die Datei sysmon.ocx enthalten ist.  Das Steuerelement ist für diese Anwendung vollständig isoliert. Diese bedeutet, dass es, wenn der Computer des Endbenutzers über eine andere Anwendung mit einer anderen Version des Steuerelements verfügt, diese Anwendung nicht beeinflussen kann.  
  
## Verweisen auf systemeigene Assemblys  
 Visual Studio unterstützt Verweise auf systemeigene Visual Basic 6.0\- oder C\+\+\-Assemblys. Solche Verweise werden auch als systemeigene Verweise bezeichnet.  Sie können feststellen, ob es sich um einen systemeigenen Verweis handelt, indem Sie überprüfen, ob seine **File Type**\-Eigenschaft auf **Systemeigen** oder **ActiveX** festgelegt ist.  
  
 Verwenden Sie zum Hinzufügen eines systemeigenen Verweises den Befehl **Verweis hinzufügen**, und wechseln Sie dann zum Manifest.  Bei einigen Komponenten befindet sich das Manifest in der DLL.  Wählen Sie in diesem Fall einfach die DLL\-Datei aus. Visual Studio fügt sie als systemeigenen Verweis hinzu, wenn diese Komponente ein eingebettetes Manifest enthält.  Visual Studio schließt außerdem automatisch alle im Manifest aufgelisteten abhängigen Dateien oder Assemblys ein, wenn sie sich im selben Ordner wie die Komponente befinden, auf die verwiesen wird.  
  
 Mit der Isolierung von COM\-Steuerelementen können auf einfache Weise COM\-Komponenten bereitgestellt werden, die noch nicht über Manifeste verfügen.  Wenn eine Komponente allerdings bereits über ein Manifest verfügt, kann direkt auf das Manifest verwiesen werden.  Tatsächlich sollten Sie statt der **Isolated**\-Eigenschaft möglichst immer das vom Autor der Komponente bereitgestellte Manifest verwenden.  
  
## Einschränkungen der Bereitstellung von COM\-Komponenten ohne Registrierung  
 Ein COM ohne Registrierung bietet klare Vorteile gegenüber traditionellen Bereitstellungsarten.  Es gibt jedoch einige Einschränkungen und Überlegungen, die zu berücksichtigen sind.  Die größte Einschränkung besteht darin, dass es erst ab Windows XP funktioniert.  Durch die Implementierung eines COM ohne Registrierung wurden Änderungen am Verfahren zum Laden von Komponenten in das Betriebssystem erforderlich.  Leider gibt es keine abwärtskompatible Unterstützung für ein COM ohne Registrierung.  
  
 Nicht jede Komponente ist für ein COM ohne Registrierung geeignet.  Eine Komponente ist nicht geeignet, wenn folgende Bedingungen vorliegen:  
  
-   Bei der Komponente handelt es sich um einen prozessexternen Server.  EXE\-Server werden nicht unterstützt, nur DLLs.  
  
-   Die Komponente ist Teil des Betriebssystems oder eine Systemkomponente wie XML, Internet Explorer oder Microsoft Data Access Components \(MDAC\).  Sie sollten der Neuverteilungsrichtlinie des Autors der Komponente folgen. Informationen dazu erhalten Sie von Ihrem Anbieter.  
  
-   Die Komponente ist Teil einer Anwendung, z. B. Microsoft Office.  Beispielsweise sollten Sie nicht versuchen, das Microsoft Excel\-Objektmodell zu isolieren.  Dabei handelt es sich um einen Teil von Office, der nur auf Computern verwendet werden kann, auf denen das vollständige Office\-Produkt installiert ist.  
  
-   Die Komponente ist zur Verwendung als Add\-In oder Snap\-In vorgesehen, z. B. als Office\-Add\-In oder als Steuerelement in einem Webbrowser.  Solche Komponenten erfordern normalerweise ein von der Hostumgebung definiertes Registrierungsschema, das sich außerhalb des Bereichs des Manifests selbst befindet.  
  
-   Die Komponente verwaltet ein physikalisches oder virtuelles Gerät für das System, z. B. einen Gerätetreiber für einen Druckerspooler.  
  
-   Die Komponente kann durch Datenzugriff umverteilt werden.  Für Datenanwendungen muss i. d. R. eine separate, durch Datenzugriff umverteilbare Komponente installiert werden, bevor diese ausgeführt werden können.  Versuchen Sie nicht, Komponenten wie das Microsoft ADO\-Datensteuerelement, Microsoft OLE DB oder Microsoft Data Access Components \(MDAC\) zu isolieren.  Wenn Ihre Anwendung MDAC oder SQL Server Express verwendet, sollten Sie diese stattdessen als erforderliche Komponente festlegen; weitere Informationen finden Sie unter [How to: Install Prerequisites with a ClickOnce Application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
 In manchen Fällen kann der Entwickler der Komponente diese für ein COM ohne Registrierung neu entwerfen.  Wenn dies nicht möglich ist, können Sie davon abhängige Anwendungen immer noch über das Standardregistrierungsschema mithilfe des Bootstrappers erstellen und veröffentlichen.  Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).  
  
 Eine COM\-Komponente kann pro Anwendung nur einmal isoliert werden.  Sie können z. B. nicht dieselbe COM\-Komponente von zwei verschiedenen **Klassenbibliothek**\-Projekten aus isolieren, die Teil derselben Anwendung sind.  Dies würde zu einer Buildwarnung führen, und die Anwendung könnte zur Laufzeit nicht geladen werden.  Um dieses Problem zu vermeiden, empfiehlt Microsoft das Kapseln von COM\-Komponenten in einer einzelnen Klassenbibliothek.  
  
 Es gibt einige Szenarios, in denen die COM\-Registrierung auf dem Computer des Entwicklers erforderlich ist, obwohl die Bereitstellung der Anwendung ohne Registrierung erfolgen kann.  Die `Isolated`\-Eigenschaft erfordert das Registrieren der COM\-Komponente auf dem Computer des Entwicklers, um das Manifest während des Builds automatisch zu generieren.  Es gibt keine Funktionen zum Aufzeichnen der Registrierung, die die Selbstregistrierung während des Builds aufrufen.  Auch werden Klassen, die nicht explizit in der Typbibliothek definiert sind, nicht im Manifest reflektiert.  Beim Verwenden einer COM\-Komponente mit einem bereits bestehenden Manifest, z. B. einem systemeigenen Verweis, muss die Komponente möglicherweise nicht zur Entwicklungszeit registriert werden.  Wenn es sich bei der Komponente allerdings um ein ActiveX\-Steuerelement handelt und Sie dieses in die **Toolbox** und in den Windows Forms\-Designer einbeziehen möchten, ist eine Registrierung erforderlich.  
  
## Siehe auch  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)