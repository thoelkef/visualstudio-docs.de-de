---
title: Bereitstellen von Com_komponenten mit ClickOnce | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 870255afe466709f8e9a5fc48e5135943443900d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001604"
---
# <a name="deploying-com-components-with-clickonce"></a>Bereitstellen von COM-Komponenten mit ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bereitstellung von älteren COM-Komponenten wurde normalerweise eine schwierige Aufgabe. Komponenten müssen global registriert werden und daher können dazu führen, dass unerwünschte Nebeneffekte zwischen überlappende Anwendungen. Dies ist in der Regel kein Problem in .NET Framework-Anwendungen, da Komponenten vollständig isoliert zu einer Anwendung werden oder Seite-an-Seite kompatibel sind. Visual Studio können Sie isolierte COM-Komponenten auf dem Windows XP oder neueren Betriebssystemen bereitgestellt.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bietet eine einfache und sichere Methode für die Bereitstellung Ihrer Anwendungen für .NET. Wenn Ihre Anwendungen auf ältere COM-Komponenten verwenden, müssen Sie jedoch weitere Schritte ausführen, für deren Bereitstellung. Dieses Thema beschreibt, wie Sie isolierte COM-Komponenten bereitstellen und systemeigene Komponenten (z. B. von Visual Basic 6.0 oder Visual C++) verweisen.  
  
 Weitere Informationen zum Bereitstellen von isolierte COM-Komponenten finden Sie unter "Simplify App Deployment with [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] und COM ohne Registrierung" auf [ https://msdn.microsoft.com/magazine/msdn-magazine-issues.aspx ](https://msdn.microsoft.com/magazine/msdn-magazine-issues.aspx).  
  
## <a name="registration-free-com"></a>COM ohne Registrierung  
 COM ohne Registrierung ist eine neue Technologie für die Bereitstellung und isolierte COM-Komponenten aktivieren. Dies erfolgt durch das Platzieren aller der Komponente Typbibliothek und Registrierungsinformationen, die in der Regel in der Registrierung des Systems in eine XML-Datei mit dem ein Manifest installiert wird im gleichen Ordner wie die Anwendung gespeichert.  
  
 Isolieren von COM-Komponente ist erforderlich, dass es auf dem Computer des Entwicklers registriert werden, aber es muss nicht auf dem Computer des Endbenutzers registriert werden. Um eine COM-Komponente zu isolieren, müssen Sie, festlegen, die des Verweis des **isoliert** Eigenschaft **"true"**. Standardmäßig ist diese Eigenschaft auf festgelegt **"false"**, gibt an, dass es als eine registrierte COM-Verweis behandelt werden soll. Wenn diese Eigenschaft **"true"**, wird ein Manifest für diese Komponente, die zum Zeitpunkt der Erstellung generiert werden soll. Es wird auch die entsprechenden Dateien in den Anwendungsordner, die während der Installation kopiert werden sollen.  
  
 Wenn der manifest-Generator eine isolierte COM-Verweises auftritt, listet er alle die `CoClass` Einträge in die Typbibliothek der Komponente, gleicht alle Einträge mit den jeweiligen Registrierungsdaten und das Generieren von Manifesten Definitionen für die COM- die Klassen in der Typbibliothek.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Bereitstellen von registrierungsfreie COM-Komponenten, die mithilfe von ClickOnce  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Technologie für die Bereitstellung eignet sich gut für die Bereitstellung von isolierten COM-Komponenten, da beide [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] und COM ohne Registrierung erfordern, dass eine Komponente ein Manifest verfügen, um bereitgestellt werden.  
  
 In der Regel sollte der Autor der Komponente ein Manifest bereitstellen. Wenn dies nicht der Fall ist, ist jedoch Visual Studio automatisch ein Manifest für eine COM-Komponente generieren kann. Die Generierung von Manifesten wird ausgeführt, während die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Veröffentlichungsprozess; Weitere Informationen finden Sie unter [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md). Dieses Feature ermöglicht es auch ältere Komponenten zu nutzen, die Sie in früheren entwicklungsumgebungen wie z. B. Visual Basic 6.0 erstellt werden soll.  
  
 Es gibt zwei Möglichkeiten, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] COM-Komponenten bereitgestellt:  
  
-   Verwenden Sie den Bootstrapper, um COM-Komponenten bereitzustellen; Dies funktioniert auf allen unterstützten Plattformen.  
  
-   Verwenden Sie die systemeigene Komponente domänenisolationsbereitstellung (auch bekannt als COM ohne Registrierung). Allerdings funktioniert dies nur auf einem Windows XP oder höheren Betriebssystem.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Beispiel zu isolieren und Bereitstellen einer einfachen COM-Komponente  
 Um die Bereitstellung von COM-Komponenten ohne Registrierung zu veranschaulichen, in diesem Beispiel erstellen Sie eine Windows-basierte Anwendung, in Visual Basic, die auf eine isolierte systemeigene COM-Komponente, die mit Visual Basic 6.0 erstellt verweist, und stellen Sie sie mithilfe [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 Zunächst müssen Sie die systemeigene COM-Komponente zu erstellen:  
  
##### <a name="to-create-a-native-com-component"></a>Um eine systemeigene COM-Komponente zu erstellen.  
  
1.  Mithilfe von Visual Basic 6.0 aus der **Datei** Menü klicken Sie auf **neu**, klicken Sie dann **Projekt**.  
  
2.  In der **neues Projekt** wählen Sie im Dialogfeld die **Visual Basic** Knoten, und wählen ein **ActiveX DLL** Projekt. Geben Sie im Feld **Name** `VB6Hello`ein.  
  
    > [!NOTE]
    >  Nur ActiveX DLL und ActiveX-Steuerelement die Projekttypen werden mit COM ohne Registrierung unterstützt. ActiveX-EXE und ActiveX-Dokument-Projekttypen werden nicht unterstützt.  
  
3.  In **Projektmappen-Explorer**, doppelklicken Sie auf **"Class1.vb"** um den Text-Editor zu öffnen.  
  
4.  In "Class1.vb", fügen Sie den folgenden Code nach dem generierten Code für die `New` Methode:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Erstellen Sie die Komponente an. Von der **erstellen** Menü klicken Sie auf **Projektmappe**.  
  
> [!NOTE]
>  COM ohne Registrierung unterstützt nur die DLLs und COM steuert Projekttypen zur Verfügung. Sie können keine EXE-Dateien mit COM ohne Registrierung verwenden.  
  
 Jetzt können Sie eine Windows-basierte Anwendung erstellen und fügen einen Verweis auf die COM-Komponente hinzu.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Zum Erstellen einer Windows-basierten Anwendung mit einer COM-Komponente  
  
1. Mit Visual Basic, aus der **Datei** Menü klicken Sie auf **neu**, klicken Sie dann **Projekt**.  
  
2. In der **neues Projekt** wählen Sie im Dialogfeld die **Visual Basic** Knoten, und wählen **Windows-Anwendung**. Geben Sie im Feld **Name** `RegFreeComDemo`ein.  
  
3. In **Projektmappen-Explorer**, klicken Sie auf die **alle Dateien anzeigen** Schaltfläche, um die Projektverweise anzuzeigen.  
  
4. Mit der rechten Maustaste die **Verweise** Knoten, und wählen **Verweis hinzufügen** aus dem Kontextmenü.  
  
5. In der **Verweis hinzufügen** Dialogfeld klicken Sie auf die **Durchsuchen** Registerkarte, navigieren Sie zu VB6Hello.dll, und wählen Sie diese.  
  
    Ein **VB6Hello** Verweis wird in der Liste der Verweise angezeigt.  
  
6. Zeigen Sie auf die **Toolbox**, wählen eine **Schaltfläche** steuern, und ziehen Sie dann auf die **Form1** Formular.  
  
7. In der **Eigenschaften** Fenster legen Sie die **Text** Eigenschaft **Hello**.  
  
8. Doppelklicken Sie auf die Schaltfläche, um Ereignishandlercode hinzufügen, und fügen Sie in der Codedatei Code hinzu, so, dass der Handler wie folgt aussieht:  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Führen Sie die Anwendung aus. Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
   Als Nächstes müssen Sie das Steuerelement zu isolieren. Jede COM-Komponente, die Ihre Anwendung verwendet wird als COM-Verweis in Ihrem Projekt dargestellt. Diese Verweise werden unter der **Verweise** Knoten in der **Projektmappen-Explorer** Fenster. (Beachten Sie, die Sie hinzufügen können die Verweise entweder direkt die **Verweis hinzufügen** Befehl die **Projekt** Menü oder indirekt durch ein ActiveX-Steuerelement auf das Formular ziehen.)  
  
   Die folgenden Schritte zeigen, wie zum Isolieren von COM-Komponente, und veröffentlichen die aktualisierte Anwendung mit dem isolierten Steuerelement:  
  
##### <a name="to-isolate-a-com-component"></a>Um eine COM-Komponente zu isolieren.  
  
1. In **Projektmappen-Explorer**in die **Verweise** Knoten die **VB6Hello** Verweis.  
  
2. In der **Eigenschaften** Fenster ändern Sie den Wert von der **isoliert** Eigenschaft **"false"** zu **"true"**.  
  
3. Von der **erstellen** Menü klicken Sie auf **Projektmappe**.  
  
   Jetzt auf, wenn Sie F5 drücken, wird die Anwendung funktioniert wie erwartet, aber es wird jetzt unter registrierungsfreies COM ausgeführt Um nachzuweisen, Aufheben der Registrierung der Komponente VB6Hello.dll, und führen RegFreeComDemo1.exe außerhalb von Visual Studio-IDE. Dieses Mal, wenn die Schaltfläche geklickt wird, funktioniert es weiterhin aus. Wenn Sie vorübergehend das Anwendungsmanifest umbenennen, tritt ein Fehler erneut.  
  
> [!NOTE]
>  Sie können das Fehlen einer COM-Komponente simulieren, indem Sie vorübergehend deren Registrierung aufheben. Öffnen Sie eine Eingabeaufforderung, wechseln Sie zu Ihrem Ordner "System", durch Eingabe `cd /d %windir%\system32`, dann heben Sie die Komponente, indem Sie eingeben `regsvr32 /u VB6Hello.dll`. Sie können es erneut registrieren, indem Sie die Eingabe `regsvr32 VB6Hello.dll`.  
  
 Der letzte Schritt ist zum Veröffentlichen der Anwendung mit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Veröffentlichen Sie ein Anwendungsupdate mit dem eine isolierte COM-Komponente  
  
1. Von der **erstellen** Menü klicken Sie auf **veröffentlichen RegFreeComDemo**.  
  
    Der Webpublishing-Assistent wird angezeigt.  
  
2. Geben Sie im Veröffentlichungs-Assistenten einen Speicherort auf dem lokalen Computer, Datenträger, in dem Sie zugreifen können, und überprüfen die veröffentlichten Dateien.  
  
3. Klicken Sie auf **Fertig stellen**, um die Anwendung zu veröffentlichen.  
  
   Wenn Sie die veröffentlichten Dateien untersuchen, werden Sie feststellen, dass die Datei dann enthalten ist. Das Steuerelement ist völlig isoliert ist, klicken Sie auf diese Anwendung, was bedeutet, dass wenn der Endbenutzer-Computer eine andere Version des Steuerelements mit einer anderen Anwendung verfügt, sie mit dieser Anwendung beeinflusst werden kann.  
  
## <a name="referencing-native-assemblies"></a>Verweisen auf die systemeigenen Assemblys  
 Visual Studio unterstützt es sich um Verweise auf systemeigene Visual Basic 6.0- oder C++-Assemblys. solche Verweise werden als native Verweise bezeichnet. Aufschluss darüber, ob ein Verweis native ist, indem Sie überprüfen, die die **Dateityp** -Eigenschaftensatz auf **Native** oder **ActiveX**.  
  
 Verwenden Sie zum Hinzufügen eines systemeigenen Verweises den **Verweis hinzufügen** Befehl aus, und navigieren Sie zu dem Manifest. Einige Komponenten platzieren Sie das Manifest in der DLL. In diesem Fall können Sie einfach die DLL selbst, und Visual Studio wird es als Hinzufügen eines systemeigenen Verweises, wenn er erkennt, dass die Komponente ein eingebettetes Manifest enthält. Visual Studio berücksichtigt auch automatisch alle abhängigen Dateien oder Assemblys, die im Manifest aufgelisteten, werden im gleichen Ordner wie die Komponente verwiesen wird.  
  
 Isolation von COM-Steuerelement erleichtert das COM-Komponenten bereitgestellt, die noch nicht über Manifeste verfügen. Wenn eine Komponente mit einem Manifest angegeben ist, können Sie das Manifest jedoch direkt verweisen. Tatsächlich sollten Sie immer das Manifest, die vom Autor der Komponente bereitgestellt wird, nach Möglichkeit anstelle von verwenden die **isoliert** Eigenschaft.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Einschränkungen der Bereitstellung von COM-Komponente ohne Registrierung  
 COM ohne Registrierung bietet klare Vorteile gegenüber herkömmlichen Bereitstellungsverfahren. Es gibt jedoch einige Einschränkungen und Einschränkungen, die auch darauf hingewiesen werden sollte. Die größte Einschränkung besteht, dass es nur unter Windows XP oder höher funktioniert. Die Implementierung von COM ohne Registrierung erforderlich, Änderungen an die Möglichkeit, die in der Komponenten in der Core-Betriebssystem geladen werden. Leider steht keine Unterstützung für kompatible-Ebene für COM ohne Registrierung  
  
 Nicht jede Komponente ist ein geeigneter Kandidat für die registrierungsfreie COM Eine Komponente ist nicht gut geeignet, wenn eine der folgenden Bedingungen zutrifft:  
  
- Die Komponente ist ein Out-of-Process-Server. EXE-Server werden nicht unterstützt. nur die DLLs werden unterstützt.  
  
- Die Komponente ist Teil des Betriebssystems oder einer Systemkomponente ein, z. B. XML, Internet Explorer oder Microsoft Data Access Components (MDAC) ist. Befolgen Sie die Richtlinie Redistribution des Autors der Komponente ein; Überprüfen Sie den Anbieter.  
  
- Die Komponente ist Teil einer Anwendung, z. B. Microsoft Office. Beispielsweise sollten Sie nicht versuchen, Microsoft Excel-Objektmodell zu isolieren. Dies ist Teil von Office und kann nur auf einem Computer mit dem vollständigen Office-Produkt installiert verwendet werden.  
  
- Die Komponente dient zur Verwendung als ein Add-in oder einem Snap-in, z. B. von einem Office-Add-in oder ein Steuerelement in einem Webbrowser. Solche Komponenten erfordern in der Regel eine Art der Registrierung des Partitionsschemas definiert, die von der hostumgebung, die das Manifest selbst nicht eingegangen ist.  
  
- Die Komponente verwaltet einen physischen oder virtuellen Gerät für das System, z. B. einen Gerätetreiber für eine Druckwarteschlange.  
  
- Die Komponente ist einer verteilbaren Datenzugriff. Data-Anwendungen erfordern in der Regel eine separate Data Access redistributable installiert werden, bevor sie ausgeführt werden können. Sie sollten nicht versuchen, zum Isolieren von Komponenten wie z. B. die Microsoft ADO-Datensteuerelement, Microsoft OLE DB oder Microsoft Data Access Components (MDAC). Wenn Ihre Anwendung MDAC oder SQL Server Express verwendet, sollten Sie diese stattdessen als erforderliche Komponenten festlegen; finden Sie unter [Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  In einigen Fällen kann es möglich, dass der Entwickler es für die registrierungsfreie COM Umgestalten der Komponente sein Wenn dies nicht möglich ist, können Sie weiterhin erstellen und Veröffentlichen von Anwendungen, die über das standard-Registrierung-Schema mithilfe des Bootstrappers abhängig. Weitere Informationen finden Sie unter [Bootstrapperpakete erstellen](../deployment/creating-bootstrapper-packages.md).  
  
  Eine COM-Komponente kann nur einmal pro Anwendung isoliert sein. Angenommen, Sie die gleiche COM-Komponente aus zwei verschiedenen isolieren können nicht **Klassenbibliothek** Projekte, die Teil derselben Anwendung sind. Dies führt zu einer Warnung, und die Anwendung kann nicht zur Laufzeit geladen. Um dieses Problem zu vermeiden, empfiehlt Microsoft, dass Sie die COM-Komponenten in einer einzigen Klassenbibliothek einkapseln.  
  
  Es gibt mehrere Szenarios, die auf die COM-Registrierung auf dem Computer des Entwicklers, erforderlich ist, obwohl die Bereitstellung der Anwendung des keine Registrierung erforderlich ist. Die `Isolated` Eigenschaft ist erforderlich, dass die COM-Komponente auf dem Computer des Entwicklers registriert werden, um das Manifest während des Buildvorgangs automatisch generieren. Sind keine Registrierung-Erfassen von Funktionen, die die selbstregistrierung während des Buildvorgangs aufrufen. Darüber hinaus werden alle Klassen, die nicht explizit definiert, in der Typbibliothek nicht im Manifest übernommen. Bei Verwendung eine COM-Komponente mit einem bereits vorhandenen Manifest, z. B. einen systemeigenen Verweis müssen die Komponente möglicherweise nicht zum Zeitpunkt der Entwicklung registriert werden. Registrierung ist jedoch erforderlich, wenn die Komponente ein ActiveX-Steuerelement ist, und es in die enthalten sein sollen die **Toolbox** und Windows Forms-Designer.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md)
