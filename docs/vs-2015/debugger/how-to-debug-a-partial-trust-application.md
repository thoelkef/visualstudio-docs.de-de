---
title: 'Vorgehensweise: Debuggen einer teilweise vertrauenswürdigen Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 030fef750cc1e0f0932de32fca1a0ffef56bc8f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704488"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Gewusst wie: Debuggen einer teilweise vertrauenswürdigen Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt für für Windows- und Konsolenanwendungen.  
  
 [ClickOnce-Sicherheit und-Bereitstellung erleichtert die Bereitstellung](../deployment/clickonce-security-and-deployment.md) teilweise vertrauenswürdiger Anwendungen, die die [Code Zugriffssicherheit](https://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) nutzen, um den Zugriff auf Ressourcen auf einem Computer einzuschränken.  
  
 Das Debuggen einer teilweise vertrauenswürdigen Anwendung ist u. U. nicht ganz einfach, weil teilweise vertrauenswürdige Anwendungen je nach Ausgangspunkt der Installation unterschiedliche Sicherheitsberechtigungen haben und sich deshalb unterschiedlich verhalten. Wenn eine teilweise vertrauenswürdige Anwendung vom Internet installiert wurde, hat sie wenige Berechtigungen. Wenn sie vom lokalen Intranet installiert wurde, hat sie mehr Berechtigungen, und wenn sie vom lokalen Computer installiert wurde, hat sie alle Berechtigungen. Außerdem haben Sie es möglicherweise mit benutzerdefinierten Zonen und entsprechenden benutzerdefinierten Berechtigungen zu tun. Unter Umständen müssen Sie eine teilweise vertrauenswürdige Anwendung unter mehreren oder allen diesen Bedingungen debuggen. Glücklicherweise erleichtert Visual Studio auch diese Aufgabe.  
  
 Bevor Sie eine Debugsitzung in Visual Studio starten, können Sie festlegen, welche Zone für die Anwendung simuliert werden soll. Beim Debuggen verfügt die Anwendung dann über die Berechtigungen für eine teilweise vertrauenswürdige Anwendung, die von dieser Zone installiert wurde. Dadurch sehen Sie, wie sich die Anwendung für einen Benutzer verhält, der sie von dieser Zone heruntergeladen hat.  
  
 Wenn die Anwendung versucht, eine Aktion auszuführen, für die sie keine Berechtigung hat, wird eine Ausnahme ausgelöst. An dieser Stelle gibt Ihnen der Ausnahmen-Assistent die Möglichkeit, eine zusätzliche Berechtigung einzufügen, sodass Sie die Debugsitzung mit ausreichenden Berechtigungen neu starten können und so das Problem vermeiden.  
  
 Später können Sie zurückgehen und sehen, welche Berechtigungen Sie während des Debuggens hinzugefügt haben. Wenn Sie während des Debuggens eine Berechtigung hinzufügen mussten, zeigt dies wahrscheinlich an, dass Sie an dieser Stelle in Ihren Code eine Meldung einfügen und den Benutzer zur Bestätigung auffordern müssen.  
  
> [!NOTE]
> Debuggerschnellansichten erfordern umfangreichere Privilegien, als sie von einer partiell vertrauenswürdigen Anwendung zugelassen werden. Schnellansichten werden nicht geladen, wenn die Ausführung in Code mit partieller Vertrauenswürdigkeit unterbrochen wurde. Wenn Sie in einer Schnellansicht debuggen möchten, müssen Sie den Code mit voller Vertrauenswürdigkeit ausführen.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>So wählen Sie eine Zone für die teilweise vertrauenswürdige Anwendung aus  
  
1. Wählen Sie im Menü **Projekt** die Option _ProjectName_-**Eigenschaften**aus.  
  
2. Klicken Sie in den Eigenschaften Seiten für *ProjectName* auf die Seite **Sicherheit** .  
  
3. Wählen Sie **ClickOnce-Sicherheitseinstellungen aktivieren**aus.  
  
4. Klicken Sie unter Zone, von der die **Anwendung installiert wird**auf das Dropdown-Listenfeld, und wählen Sie die Zone aus, in der die Anwendung simuliert werden soll, aus der die Anwendung installiert wird  
  
     Die **für das Anwendungs Raster erforderlichen Berechtigungen** zeigen alle verfügbaren Berechtigungen an. Das Häkchen zeigt an, welche Berechtigungen die Anwendung besitzt.  
  
5. Wenn Sie die ausgewählte Zone **(Benutzer definiert)** ausgewählt haben, wählen Sie die richtigen benutzerdefinierten Einstellungen in der **Einstellungs** Spalte des Raster **Berechtigungen** aus.  
  
6. Klicken Sie auf **OK**, um die Eigenschaftenseiten zu schließen.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>So fügen Sie eine zusätzliche Berechtigung hinzu, wenn eine Sicherheitsausnahme eintritt  
  
1. Das Dialogfeld **Ausnahmen-Assistent** wird mit der folgenden Meldung angezeigt: **SecurityException wurde nicht behandelt.**  
  
2. Klicken Sie im Dialogfeld **Ausnahmen-Assistent** unter **Aktionen** **auf Berechtigung zum Projekt hinzufügen**.  
  
3. Das Dialogfeld **Debuggen neu starten** wird angezeigt.  
  
    - Wenn Sie die Debugsitzung mit der neuen Berechtigung neu starten möchten, klicken Sie auf **Ja**.  
  
    - Wenn Sie noch nicht neu starten möchten, klicken Sie auf **Nein**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>So zeigen Sie zusätzliche Berechtigungen an, die beim Debuggen hinzugefügt wurden  
  
1. Wählen Sie im Menü **Projekt** die Option _ProjectName_-**Eigenschaften**aus.  
  
2. Klicken Sie in den Eigenschaften Seiten für *ProjectName* auf die Seite **Sicherheit** .  
  
3. Sehen Sie sich die **für das Anwendungs Raster erforderlichen Berechtigungen** an. Alle zusätzlichen Berechtigungen, die Sie hinzugefügt haben, weisen zwei Symbole in der Spalte " **eingeschlossen** " auf: das normale Häkchen, das alle enthaltenen Berechtigungen besitzen, und ein zusätzliches Symbol, das wie eine Sprechblase mit dem Buchstaben "i" aussieht.  
  
4. Verwenden Sie die vertikale Bild Lauf Leiste, um die gesamten Berechtigungen anzuzeigen, die **vom Anwendungs Raster benötigt werden** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Sicherheit und-Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)
