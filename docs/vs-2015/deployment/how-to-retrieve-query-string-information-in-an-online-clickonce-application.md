---
title: 'Vorgehensweise: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8239b0ccbedfdb2965d8dc5f7738c50f9548e94
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431504"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Vorgehensweise: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die *Abfragezeichenfolge* ist der Teil einer URL, die mit einem Fragezeichen (?) beginnt und die willkürliche Informationen im Format *name=value*enthält. Angenommen, Sie verfügen über eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung mit dem Namen `WindowsApp1` , die Sie auf `servername`hosten, und Sie möchten einen Wert für die Variable `username` bei Anwendungsstart übergeben. Die URL könnte folgendermaßen aussehen:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Die folgenden zwei Vorgehensweisen zeigen, wie eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung verwendet wird, um Informationen über Abfragezeichenfolgen abzurufen.  
  
> [!NOTE]
> Sie können nur Informationen in einer Abfragezeichenfolge übergeben, wenn Ihre Anwendung über HTTP gestartet wird und nicht über eine Dateifreigabe oder das lokale Dateisystem.  
  
 Das erste Verfahren zeigt, wie Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung einen kleinen Codeabschnitt verwenden kann, um diese Werte bei Anwendungsstart zu lesen.  
  
 Das nächste Verfahren zeigt, wie Sie Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung mithilfe MageUI.exe so konfigurieren, dass sie Abfragezeichenfolgen-Parameter akzeptieren kann. Sie müssen dieses Verfahren bei jeder Veröffentlichung der Anwendung durchführen.  
  
> [!NOTE]
> Bevor Sie eine Entscheidung zur Aktivierung dieser Funktion treffen, lesen Sie zuerst den Abschnitt „Sicherheit“ weiter unten in diesem Thema.  
  
 Informationen zum Erstellen einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Bereitstellung mit Mage.exe oder MageUI.exe, finden Sie unter [Exemplarische Vorgehensweise: Manually Deploying a ClickOnce Application (Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung)](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
> Ab .NET Framework 3.5 SP1 ist es möglich, Befehlszeilenargumente an eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Offlineanwendung zu übergeben. Wenn Sie der Anwendung Argumente bereitstellen möchten, können Sie der Verknüpfungsdatei In-Parameter mit der Erweiterung APPREF-MS übergeben.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>So rufen Sie Abfragezeichenfolgen-Informationen in einer ClickOnce-Anwendung ab  
  
1. Platzieren Sie folgenden Code in Ihrem Projekt. Damit dieser Code funktioniert, müssen Sie über einen Verweis auf System.Web verfügen und `using` - oder `Imports` -Anweisungen für System.Web, System.Collections.Specialized und System.Deployment.Application hinzufügen.  
  
     [!code-csharp[ClickOnceQueryString#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceQueryString/CS/Form1.cs#1)]
     [!code-vb[ClickOnceQueryString#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceQueryString/VB/Form1.vb#1)]  
  
2. Rufen Sie die zuvor definierte Funktion ab, um ein nach Namen indexiertes <xref:System.Collections.DictionaryBase.Dictionary%2A> der Abfragezeichenfolgenparameter abzurufen.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>So aktivieren Sie die Übergabe der Abfragezeichenfolge in einer ClickOnce-Anwendung mit MageUI.exe  
  
1. Öffnen Sie die Eingabeaufforderung .NET und geben Sie Folgendes ein:  
  
    ```  
    MageUI  
    ```  
  
2. Wählen Sie im Menü **Datei** die Option **Öffnen**aus, und öffnen Sie das Bereitstellungsmanifest für Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung, die die Dateiendung `.application` aufweist.  
  
3. Wählen Sie den Bereich **Bereitstellungsoptionen** im linken Navigationsfenster aus, und wählen Sie das Kontrollkästchen **Übergeben von URL-Parametern an die Anwendung zulassen** aus.  
  
4. Wählen Sie im Menü **Datei** die Option **Speichern**aus.  
  
> [!NOTE]
> Sie können alternativ die Übergabe der Abfragezeichenfolge in [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]aktivieren. Wählen Sie das Kontrollkästchen **Übergeben von URL-Parametern an die Anwendung zulassen** aus. Dieses Kontrollkästchen finden Sie, indem Sie die **Projekteigenschaften**öffnen und die Schaltfläche **Veröffentlichen** auswählen. Anschließend klicken Sie auf die Schaltfläche **Optionen** und wählen **Manifeste**aus.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Wenn Sie Abfragezeichenfolgen-Parameter verwenden, überlegen Sie genau, wie Ihre Anwendung installiert und aktiviert wird. Wenn Ihre Anwendung so konfiguriert ist, dass Sie auf dem Computer des Nutzers aus dem Web oder einer Netzwerkfreigabe installiert wird, dann ist es wahrscheinlich, dass der Benutzer die Anwendung nur einmal über die URL aktivieren wird. Danach aktiviert der Benutzer Ihre Anwendung normalerweise über die Verknüpfung im Menü **Start** . Deshalb ist gewährleistet, dass Ihre Anwendung Argumente für Abfragezeichenfolgen nur einmal im Laufe ihrer Lebensdauer erhält. Wenn Sie diese Argumente auf dem Computer des Benutzers für den zukünftigen Gebrauch speichern möchten, sind Sie dafür verantwortlich, sie auf sichere Weise zu speichern.  
  
 Wenn Ihre Anwendung nur online ist, wird sie immer durch eine URL aktiviert. Allerdings muss Ihre Anwendung auch in diesem Fall so geschrieben werden, dass sie ordnungsgemäß funktioniert, wenn die Abfragezeichenfolgen-Parameter fehlen oder beschädigt sind.  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Lassen Sie die Übergabe von URL-Parametern an Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung nur zu, wenn Sie beabsichtigen, die Eingabe von böswilligen Zeichen vor der Verwendung zu bereinigen. Eine Zeichenfolge, die z.B. mit Anführungszeichen, Schrägstrichen oder Semikola als Trennzeichen eingebettet ist, kann möglicherweise willkürliche Datenvorgänge durchführen, wenn sie ungefiltert in einer SQL-Abfrage für eine Datenbank verwendet wird. Weitere Informationen zur Sicherheit von Abfragezeichenfolgen finden Sie unter [Script Exploits Overview](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
