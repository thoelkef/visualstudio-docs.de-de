---
title: COM-Komponenten mit ClickOnce-Bereitstellung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab25276596358f7c0a8c1f90bd38e89686e3196c
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815872"
---
# <a name="deploying-com-components-with-clickonce"></a>Bereitstellen von COM-Komponenten mit ClickOnce
Bereitstellung von älteren COM-Komponenten war bisher, dass eine schwierige Aufgabe. Komponenten müssen global registriert werden und daher können dazu führen, dass unerwünschte Nebeneffekte zwischen überlappende Anwendungen. Diese Situation ist in der Regel kein Problem in .NET Framework-Anwendungen, da Komponenten vollständig isoliert zu einer Anwendung sind oder die Seite-an-Seite kompatibel sind. Visual Studio können Sie isolierte COM-Komponenten auf dem Windows XP oder höher Betriebssystem bereitstellen.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bietet einen einfachen und sicheren Mechanismus für das Bereitstellen von. Wenn Ihre Anwendung legacy-COM-Komponenten verwenden, müssen Sie zusätzliche Schritte ausführen, für deren Bereitstellung. In diesem Thema wird beschrieben, wie zum Bereitstellen von isolierter COM-Komponenten und systemeigene Komponenten (z. B. von Visual Basic 6.0 oder Visual C++) verweisen wird.  
  
 Weitere Informationen zum Bereitstellen von isolierte COM-Komponenten finden Sie unter "App-Bereitstellung mit vereinfachten [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] und COM ohne Registrierung" am [ http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx ](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## <a name="registration-free-com"></a>COM ohne Registrierung  
 COM ohne Registrierung ist eine neue Technologie für die Bereitstellung und Aktivierung isolierte COM-Komponenten. Es funktioniert, indem die Inkonsistenzen Typbibliothek für alle der Komponente und Registrierungsinformationen, die in der Regel in der systemregistrierung in eine XML-Datei mit dem Namen ein Manifest installiert wird im gleichen Ordner wie die Anwendung gespeichert.  
  
 Isolieren von COM-Komponente ist erforderlich, dass er auf dem Computer des Entwicklers registriert werden, aber es muss keine auf dem Computer des Endbenutzers registriert werden. Um eine COM-Komponente zu isolieren, müssen Sie, festlegen, die des Verweis **isoliert** Eigenschaft **"true"**. Standardmäßig ist diese Eigenschaft auf festgelegt **"false"**, gibt an, dass es als registrierten COM-Verweis behandelt werden sollen. Wenn diese Eigenschaft ist **"true"**, er bewirkt, dass ein Manifest für diese Komponente, die während des Buildvorgangs generiert werden soll. Er führt dazu, dass die entsprechenden Dateien auf den Anwendungsordner, die während der Installation kopiert werden sollen.  
  
 Wenn der manifest-Generator einen isolierte COM-Verweis trifft, listet er alle die `CoClass` Einträge in der Typbibliothek der Komponente, jeder Eintrag mit den entsprechenden Registrierungsdaten Abgleich und Generieren von Manifesten Definitionen für die COM- die Klassen in der Typbibliothek.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Bereitstellung von registrierungsfreie Com_komponenten mit ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitstellungstechnologie eignet sich gut für isolierte COM-Komponenten bereitstellen, da beide [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] und COM ohne Registrierung erforderlich ist, dass eine Komponente ein Manifest aufweisen, damit die bereitgestellt werden.  
  
 Der Autor der Komponente sollte in der Regel ein Manifest bereitstellen. Wenn dies nicht der Fall ist, ist jedoch Visual Studio automatisch ein Manifest für eine COM-Komponente generieren kann. Die Generierung von Manifesten erfolgt während der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Veröffentlichungsprozess; Weitere Informationen finden Sie unter [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md). Diese Funktion ermöglicht zudem das Legacykomponenten nutzen, die Sie in früheren entwicklungsumgebungen wie z. B. Visual Basic 6.0 erstellt wurden.  
  
 Es gibt zwei Möglichkeiten, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] COM-Komponenten bereitgestellt:  
  
-   Verwenden des Bootstrappers zum Bereitstellen von COM-Komponenten. Dies funktioniert auf allen unterstützten Plattformen.  
  
-   Verwenden Sie systemeigene Komponente Isolation (auch bekannt als registrierungsfreie COM)-Bereitstellung. Dies kann jedoch nur auf einem Windows XP oder höher Betriebssystem verwendet.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Beispiel für isolieren und Bereitstellen einer einfachen COM-Komponente  
 Um registrierungsfreie COM-komponentenbereitstellung zu veranschaulichen, in diesem Beispiel erstellen Sie eine Windows-basierte Anwendung in Visual Basic, die auf eine isolierte systemeigene COM-Komponente, die mit Visual Basic 6.0 erstellte verweist, und Bereitstellen mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Zuerst müssen Sie die systemeigene COM-Komponente zu erstellen:  
  
##### <a name="to-create-a-native-com-component"></a>So erstellen eine systemeigene COM‑Komponente  
  
1.  Mithilfe von Visual Basic 6.0, von der **Datei** Menü klicken Sie auf **neu**, klicken Sie dann **Projekt**.  
  
2.  In der **neues Projekt** wählen Sie im Dialogfeld die **Visual Basic** Knoten, und wählen eine **ActiveX DLL** Projekt. Geben Sie im Feld **Name** `VB6Hello`ein.  
  
    > [!NOTE]
    >  Nur für ActiveX-DLL und ActiveX-Steuerelement-Projekttypen werden mit COM ohne Registrierung unterstützt. ActiveX-EXE und ActiveX-Dokument-Projekttypen werden nicht unterstützt.  
  
3.  In **Projektmappen-Explorer**, doppelklicken Sie auf **Class1.vb** auf den Texteditor zu öffnen.  
  
4.  Fügen Sie den folgenden Code in Class1.vb nach dem generierten Code für die `New` Methode:  
  
    ```vb  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Erstellen Sie die Komponente. Aus der **erstellen** Menü klicken Sie auf **Projektmappe**.  
  
> [!NOTE]
>  COM ohne Registrierung unterstützt nur DLLs und COM steuert Projekttypen zur Verfügung. Sie können keine EXE-Dateien mit registrierungsfreies verwenden.  
  
 Jetzt können Sie eine Windows-basierte Anwendung erstellen und ihm einen Verweis auf die COM-Komponente hinzugefügt.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>So erstellen eine Windows-basierte Anwendung, die mithilfe einer COM‑Komponente  
  
1.  Mit Visual Basic, aus der **Datei** Menü klicken Sie auf **neu**, klicken Sie dann **Projekt**.  
  
2.  In der **neues Projekt** wählen Sie im Dialogfeld die **Visual Basic** Knoten, und wählen **Windows-Anwendung**. Geben Sie im Feld **Name** `RegFreeComDemo`ein.  
  
3.  In **Projektmappen-Explorer**, klicken Sie auf die **alle Dateien anzeigen** Schaltfläche, um die Projektverweise anzuzeigen.  
  
4.  Mit der rechten Maustaste die **Verweise** Knoten, und wählen **Verweis hinzufügen** aus dem Kontextmenü.  
  
5.  In der **Verweis hinzufügen** (Dialogfeld), klicken Sie auf die **Durchsuchen** Registerkarte, navigieren Sie zu VB6Hello.dll, und wählen Sie es.  
  
     Ein **VB6Hello** Verweis in der Liste der Verweise wird angezeigt.  
  
6.  Zeigen Sie auf die **Toolbox**, wählen eine **Schaltfläche** steuern, und ziehen Sie auf der **Form1** Formular.  
  
7.  In der **Eigenschaften** legen der Schaltfläche **Text** Eigenschaft **Hello**.  
  
8.  Doppelklicken Sie auf die Schaltfläche, um Ereignishandlercode hinzufügen, und fügen Sie Code in der Codedatei, damit der Ereignishandler wie folgt aussieht:  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Führen Sie die Anwendung aus. Aus der **Debuggen** Menü klicken Sie auf **Debuggen**.  
  
 Als Nächstes müssen Sie das Steuerelement zu isolieren. Jede COM-Komponente, die Ihre Anwendung verwendet wird als COM-Verweis im Projekt dargestellt. Diese Verweise werden unter der **Verweise** Knoten in der **Projektmappen-Explorer** Fenster. (Beachten Sie, die Sie hinzufügen können verweist, entweder direkt mit der **Verweis hinzufügen** Befehl die **Projekt** Menü oder indirekt durch ein ActiveX-Steuerelement auf das Formular ziehen.)  
  
 Die folgenden Schritte zeigen, wie die COM-Komponente zu isolieren und veröffentlichen die aktualisierte Anwendung, die die isolierte Steuerelement enthält:  
  
##### <a name="to-isolate-a-com-component"></a>Um eine COM-Komponente zu isolieren.  
  
1.  In **Projektmappen-Explorer**in der **Verweise** Knoten, wählen die **VB6Hello** Verweis.  
  
2.  In der **Eigenschaften** Fenster, ändern Sie den Wert von der **isoliert** Eigenschaft aus **"false"** auf **"true"**.  
  
3.  Aus der **erstellen** Menü klicken Sie auf **Projektmappe**.  
  
 Jetzt auf, wenn Sie F5 drücken, wird die Anwendung funktioniert wie erwartet, aber es wird nun unter registrierungsfreies ausgeführt Um nachzuweisen, versuchen Sie es beim Aufheben der Registrierung der Komponente VB6Hello.dll und RegFreeComDemo1.exe außerhalb der Visual Studio-IDE ausgeführt. Dieses Mal, wenn die Schaltfläche geklickt wird, weiterhin funktioniert. Wenn Sie das Anwendungsmanifest vorübergehend umbenennen, wird er wieder ein Failover ausgeführt.  
  
> [!NOTE]
>  Sie können das Fehlen einer COM-Komponente simulieren, indem Sie vorübergehend deren Registrierung aufheben. Öffnen Sie ein Eingabeaufforderungsfenster, wechseln Sie zu Ihrem Ordner "System" dazu `cd /d %windir%\system32`, heben Sie dazu die Registrierung der Komponente `regsvr32 /u VB6Hello.dll`. Sie können ihn erneut registrieren, durch Eingabe `regsvr32 VB6Hello.dll`.  
  
 Der letzte Schritt ist zum Veröffentlichen der Anwendung über [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>So veröffentlichen Sie ein Anwendungsupdate mit dem eine isolierte COM‑Komponente  
  
1.  Aus der **erstellen** Menü klicken Sie auf **RegFreeComDemo veröffentlichen**.  
  
     Der Webpublishing-Assistent wird angezeigt.  
  
2.  Geben Sie im Veröffentlichungs-Assistenten einen Speicherort auf dem lokalen Computer Datenträger können Sie Zugriff auf und untersuchen Sie die veröffentlichten Dateien.  
  
3.  Klicken Sie auf **Fertig stellen** veröffentlichen die Anwendung.  
  
 Wenn Sie die veröffentlichten Dateien untersuchen, werden Sie bemerken, dass die Datei dann enthalten ist. Das Steuerelement ist vollkommen isoliert ist, um diese Anwendung, d. h., wenn der Endbenutzer-Computer eine andere Version des Steuerelements mit einer anderen Anwendung hat, es mit dieser Anwendung beeinflusst werden kann.  
  
## <a name="referencing-native-assemblies"></a>Verweisen auf systemeigene Assemblys  
 Visual Studio unterstützt Verweise auf systemeigene Visual Basic 6.0- oder C++-Assemblys. solche Verweise werden als systemeigene Verweise bezeichnet. Ist ersichtlich, ob ein Verweis überprüfen, ob systemeigene ist seine **Dateityp** -Eigenschaftensatz auf **Native** oder **ActiveX**.  
  
 Um ein systemeigener Verweis hinzuzufügen, verwenden Sie die **Verweis hinzufügen** Befehl, und navigieren Sie zu dem Manifest. Einige Komponenten platzieren Sie das Manifest in die DLL-Datei. In diesem Fall können Sie einfach die DLL selbst auswählen und Visual Studio fügt er als ein systemeigener Verweis würde er erkennt, dass die Komponente kein eingebettetes Manifest enthält. Visual Studio schließt außerdem automatisch alle abhängigen Dateien oder Assemblys, die im Manifest aufgelisteten, werden im gleichen Ordner wie die Komponente, auf die verwiesen wird.  
  
 COM-Steuerelement Isolation erleichtert die COM-Komponenten bereitstellen, die noch nicht über Manifeste verfügen. Wenn eine Komponente mit einem Manifest angegeben wird, können Sie das Manifest jedoch direkt verweisen. Tatsächlich sollten Sie immer das Manifest vom Autor der Komponente bereitgestellt wird, nach Möglichkeit anstelle von verwenden die **isoliert** Eigenschaft.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Einschränkungen der COM-Komponente ohne Registrierung-Bereitstellung  
 COM ohne Registrierung bietet klare Vorteile gegenüber herkömmlichen Bereitstellungsverfahren. Es gibt jedoch einige Einschränkungen und Fallstricke, die auch darauf hingewiesen werden sollte. Die größte Beschränkung ist, dass es nur unter Windows XP oder höher. Die Implementierung von COM ohne Registrierung erforderlich sind, ändert sich die Art und Weise, in der Komponenten in die Core-Betriebssystem geladen werden. Leider besteht keine Unterstützung früherer-Ebene für registrierungsfreies  
  
 Nicht jede Komponente ist ein geeigneter Kandidat für die registrierungsfreie COM Eine Komponente ist nicht gut geeignet, wenn Folgendes zutrifft:  
  
-   Die Komponente ist ein Out-of-Process-Server. EXE-Server werden nicht unterstützt. nur DLLs werden unterstützt.  
  
-   Die Komponente ist Teil des Betriebssystems oder eine Systemkomponente, z. B. XML, Internet Explorer oder Microsoft Data Access Components (MDAC) ist. Befolgen Sie die Richtlinie Redistribution des Autors der Komponente ein; Wenden Sie sich an den Anbieter.  
  
-   Die Komponente ist Teil einer Anwendung, z. B. Microsoft Office. Beispielsweise sollten Sie nicht versuchen, Microsoft Excel-Objektmodell zu isolieren. Dies ist der Teil von Office und kann nur auf einem Computer mit dem vollständigen Office-Produkt installiert verwendet werden.  
  
-   Die Komponente dient zur Verwendung als ein Add-in oder ein Snap-in, z. B. von einem Office-Add-in oder ein Steuerelement in einem Webbrowser. Solche Komponenten erfordern in der Regel eine Art der Registrierung des Partitionsschemas von der hostumgebung, die nicht Gegenstand des Manifests selbst ist definiert.  
  
-   Die Komponente verwaltet eine physische oder virtuelle Geräte für das System, z. B. ein Gerätetreiber für eine Druckwarteschlange.  
  
-   Die Komponente ist eine verteilbare Datenzugriff. Datenanwendungen erfordern in der Regel eine separate Datenzugriffs redistributable installiert werden, bevor sie ausgeführt werden können. Sie sollten nicht versuchen, um Komponenten wie Microsoft ADO-Datensteuerelement, Microsoft OLE DB oder Microsoft Data Access Components (MDAC) zu isolieren. Wenn Ihre Anwendung MDAC oder SQL Server Express verwendet, sollten Sie diese stattdessen als erforderliche Komponenten festlegen; finden Sie unter [Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
 In einigen Fällen kann es möglich, dass der Entwickler der Komponente, die sie für die registrierungsfreie COM eine bessere sein Wenn dies nicht möglich ist, können Sie erstellen und Veröffentlichen von Anwendungen, die über das standard-Registrierung-Schema mithilfe des Bootstrappers abhängig. Weitere Informationen finden Sie unter [Bootstrapperpakete erstellen](../deployment/creating-bootstrapper-packages.md).  
  
 Eine COM-Komponente kann nur einmal pro Anwendung isoliert sein. Beispielsweise kann nicht zu die gleiche COM-Komponente aus zwei verschiedenen isolieren **-Klassenbibliothek** Projekte, die Teil der gleichen Anwendung sind. Auf diese Weise führt eine Buildwarnung aus, und die Anwendung wird nicht zur Laufzeit geladen. Um dieses Problem zu vermeiden, empfiehlt Microsoft, dass Sie COM-Komponenten in einer einzelnen Klassenbibliothek kapseln.  
  
 Es gibt mehrere Szenarien, die auf die COM-Registrierung auf dem Computer des Entwicklers, erforderlich ist, obwohl die Bereitstellung der Anwendung keine Registrierung erforderlich ist. Die `Isolated` Eigenschaft ist erforderlich, dass die COM-Komponente auf dem Computer des Entwicklers registriert werden, um das Manifest während der Erstellung automatisch generiert. Es gibt keine Registrierung erfassen-Funktionen, mit die die Self-Registrierung während des Erstellungsvorgangs aufgerufen. Darüber hinaus werden alle Klassen, die nicht explizit in der Typbibliothek definiert im Manifest nicht berücksichtigt. Bei Verwendung eine COM-Komponente mit einem bereits vorhandenen Manifest, z. B. ein systemeigener Verweis kann die Komponente nicht zur Entwicklungszeit registriert werden müssen. Registrierung ist jedoch erforderlich, wenn die Komponente ein ActiveX-Steuerelement ist, und Sie zur Einbindung in möchten die **Toolbox** und Windows Forms-Designer.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md)