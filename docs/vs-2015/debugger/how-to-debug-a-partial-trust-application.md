---
title: 'Vorgehensweise: Debuggen eine teilweise vertrauenswürdigen Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b3b7bb7e880b30e975770ee35dfb537e62827b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288222"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Gewusst wie: Debuggen einer teilweise vertrauenswürdigen Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt für für Windows- und Konsolenanwendungen.  
  
 [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md) erleichtert Ihnen die teilweise vertrauenswürdige Anwendungen bereitstellen, die nutzen [Code Access Security](http://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) den Zugriff auf Ressourcen auf einem Computer einschränken.  
  
 Das Debuggen einer teilweise vertrauenswürdigen Anwendung ist u. U. nicht ganz einfach, weil teilweise vertrauenswürdige Anwendungen je nach Ausgangspunkt der Installation unterschiedliche Sicherheitsberechtigungen haben und sich deshalb unterschiedlich verhalten. Wenn eine teilweise vertrauenswürdige Anwendung vom Internet installiert wurde, hat sie wenige Berechtigungen. Wenn sie vom lokalen Intranet installiert wurde, hat sie mehr Berechtigungen, und wenn sie vom lokalen Computer installiert wurde, hat sie alle Berechtigungen. Außerdem haben Sie es möglicherweise mit benutzerdefinierten Zonen und entsprechenden benutzerdefinierten Berechtigungen zu tun. Unter Umständen müssen Sie eine teilweise vertrauenswürdige Anwendung unter mehreren oder allen diesen Bedingungen debuggen. Glücklicherweise erleichtert Visual Studio auch diese Aufgabe.  
  
 Bevor Sie eine Debugsitzung in Visual Studio starten, können Sie festlegen, welche Zone für die Anwendung simuliert werden soll. Beim Debuggen verfügt die Anwendung dann über die Berechtigungen für eine teilweise vertrauenswürdige Anwendung, die von dieser Zone installiert wurde. Dadurch sehen Sie, wie sich die Anwendung für einen Benutzer verhält, der sie von dieser Zone heruntergeladen hat.  
  
 Wenn die Anwendung versucht, eine Aktion auszuführen, für die sie keine Berechtigung hat, wird eine Ausnahme ausgelöst. An dieser Stelle gibt Ihnen der Ausnahmen-Assistent die Möglichkeit, eine zusätzliche Berechtigung einzufügen, sodass Sie die Debugsitzung mit ausreichenden Berechtigungen neu starten können und so das Problem vermeiden.  
  
 Später können Sie zurückgehen und sehen, welche Berechtigungen Sie während des Debuggens hinzugefügt haben. Wenn Sie während des Debuggens eine Berechtigung hinzufügen mussten, zeigt dies wahrscheinlich an, dass Sie an dieser Stelle in Ihren Code eine Meldung einfügen und den Benutzer zur Bestätigung auffordern müssen.  
  
> [!NOTE]
>  Debuggerschnellansichten erfordern umfangreichere Privilegien, als sie von einer partiell vertrauenswürdigen Anwendung zugelassen werden. Schnellansichten werden nicht geladen, wenn die Ausführung in Code mit partieller Vertrauenswürdigkeit unterbrochen wurde. Wenn Sie in einer Schnellansicht debuggen möchten, müssen Sie den Code mit voller Vertrauenswürdigkeit ausführen.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>So wählen Sie eine Zone für die teilweise vertrauenswürdige Anwendung aus  
  
1.  Von der **Projekt** Menü wählen _Projectname_**Eigenschaften**.  
  
2.  In der *Projectname* Eigenschaftenseiten, klicken Sie auf die **Sicherheit** Seite.  
  
3.  Wählen Sie **ClickOnce-Sicherheitseinstellungen aktivieren**.  
  
4.  Klicken Sie unter **Zone, die von Ihrer Anwendung installiert werden**, klicken Sie auf das Dropdown-Listenfeld, und wählen Sie die Zone, die Sie der Anwendung simulieren möchten.  
  
     Die **Berechtigungen, die von der Anwendung benötigten** Raster zeigt alle verfügbare Berechtigungen. Das Häkchen zeigt an, welche Berechtigungen die Anwendung besitzt.  
  
5.  Bei die Zone, die Sie auswählen, **(Benutzerdefiniert)**, wählen Sie die korrekten benutzerdefinierten Einstellungen in der **Einstellung** Spalte die **Berechtigungen** Raster.  
  
6.  Klicken Sie auf **OK**, um die Eigenschaftenseiten zu schließen.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>So fügen Sie eine zusätzliche Berechtigung hinzu, wenn eine Sicherheitsausnahme eintritt  
  
1.  Die **Ausnahmen-Assistent** Dialogfeld wird angezeigt, mit der Meldung: **SecurityException wurde nicht behandelt.**  
  
2.  In der **Ausnahmen-Assistent** Dialogfeld **Aktionen**, klicken Sie auf **Berechtigung hinzufügen, um das Projekt**.  
  
3.  Die **Debuggen neu starten** Dialogfeld wird angezeigt.  
  
    -   Wenn Sie die Debugsitzung mit der neuen Berechtigung neu starten möchten, klicken Sie auf **Ja**.  
  
    -   Wenn Sie nicht noch neu starten möchten, klicken Sie auf **keine**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>So zeigen Sie zusätzliche Berechtigungen an, die beim Debuggen hinzugefügt wurden  
  
1.  Von der **Projekt** Menü wählen _Projectname_**Eigenschaften**.  
  
2.  In der *Projectname* Eigenschaftenseiten, klicken Sie auf die **Sicherheit** Seite.  
  
3.  Sehen Sie sich die **Berechtigungen, die von der Anwendung benötigten** Raster. Alle von Ihnen hinzugefügte zusätzliche Berechtigung hat zwei Symbole in der **eingeschlossene** Spalte: das normale Häkchen, das alle eingeschlossenen Berechtigungen aufweisen, und ein zusätzliches Symbol, etwa eine Sprechblase mit dem Buchstaben "i".  
  
4.  Verwenden Sie die vertikale scrollleiste, um die gesamte anzuzeigen **Berechtigungen, die von der Anwendung benötigten** Raster.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)



