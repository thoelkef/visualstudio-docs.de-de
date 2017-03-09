---
title: "Gewusst wie: Debuggen einer teilweise vertrauensw&#252;rdigen Anwendung | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Teilweise vertrauenswürdige Anwendungen"
  - "Teilweise vertrauenswürdige Anwendungen"
  - "Sicherheit [Visual Studio], Teilweise vertrauenswürdige Anwendungen"
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Debuggen einer teilweise vertrauensw&#252;rdigen Anwendung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gilt für für Windows\- und Konsolenanwendungen.  
  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md) erleichtert das Bereitstellen von teilweise vertrauenswürdigen Anwendungen, die mithilfe von [Code Access Security](../Topic/Code%20Access%20Security.md) den Zugriff auf die Ressourcen eines Computers einschränken.  
  
 Das Debuggen einer teilweise vertrauenswürdigen Anwendung ist u. U. nicht ganz einfach, weil teilweise vertrauenswürdige Anwendungen je nach Ausgangspunkt der Installation unterschiedliche Sicherheitsberechtigungen haben und sich deshalb unterschiedlich verhalten.  Wenn eine teilweise vertrauenswürdige Anwendung vom Internet installiert wurde, hat sie wenige Berechtigungen.  Wenn sie vom lokalen Intranet installiert wurde, hat sie mehr Berechtigungen, und wenn sie vom lokalen Computer installiert wurde, hat sie alle Berechtigungen.  Außerdem haben Sie es möglicherweise mit benutzerdefinierten Zonen und entsprechenden benutzerdefinierten Berechtigungen zu tun.  Unter Umständen müssen Sie eine teilweise vertrauenswürdige Anwendung unter mehreren oder allen diesen Bedingungen debuggen.  Glücklicherweise erleichtert Visual Studio auch diese Aufgabe.  
  
 Bevor Sie eine Debugsitzung in Visual Studio starten, können Sie festlegen, welche Zone für die Anwendung simuliert werden soll.  Beim Debuggen verfügt die Anwendung dann über die Berechtigungen für eine teilweise vertrauenswürdige Anwendung, die von dieser Zone installiert wurde.  Dadurch sehen Sie, wie sich die Anwendung für einen Benutzer verhält, der sie von dieser Zone heruntergeladen hat.  
  
 Wenn die Anwendung versucht, eine Aktion auszuführen, für die sie keine Berechtigung hat, wird eine Ausnahme ausgelöst.  An dieser Stelle gibt Ihnen der Ausnahmen\-Assistent die Möglichkeit, eine zusätzliche Berechtigung einzufügen, sodass Sie die Debugsitzung mit ausreichenden Berechtigungen neu starten können und so das Problem vermeiden.  
  
 Später können Sie zurückgehen und sehen, welche Berechtigungen Sie während des Debuggens hinzugefügt haben.  Wenn Sie während des Debuggens eine Berechtigung hinzufügen mussten, zeigt dies wahrscheinlich an, dass Sie an dieser Stelle in Ihren Code eine Meldung einfügen und den Benutzer zur Bestätigung auffordern müssen.  
  
> [!NOTE]
>  Debuggerschnellansichten erfordern umfangreichere Privilegien, als sie von einer partiell vertrauenswürdigen Anwendung zugelassen werden.  Schnellansichten werden nicht geladen, wenn die Ausführung in Code mit partieller Vertrauenswürdigkeit unterbrochen wurde.  Wenn Sie in einer Schnellansicht debuggen möchten, müssen Sie den Code mit voller Vertrauenswürdigkeit ausführen.  
  
### So wählen Sie eine Zone für die teilweise vertrauenswürdige Anwendung aus  
  
1.  Klicken Sie im Menü **Projekt** für *Projectname* auf **Eigenschaften**.  
  
2.  Klicken Sie auf den *Projectname*\-Eigenschaftenseiten auf die Seite **Sicherheit**.  
  
3.  Wählen Sie **ClickOnce\-Sicherheitseinstellungen aktivieren**.  
  
4.  Klicken Sie unter **Zone, aus der die Anwendung installiert wird** auf das Dropdown\-Listenfeld, und wählen die Zone, die probehalber als Herkunftszone der Anwendung zugrunde gelegt werden soll.  
  
     Das Datenblatt **Von der Anwendung benötigte Berechtigungen** zeigt alle verfügbaren Berechtigungen an.  Das Häkchen zeigt an, welche Berechtigungen die Anwendung besitzt.  
  
5.  Wenn Sie als Zone **\(Benutzerdefiniert\)** auswählen, wählen Sie im Datenblatt **Berechtigungen** in der Spalte **Einstellung** die korrekten benutzerdefinierten Einstellungen aus.  
  
6.  Klicken Sie auf **OK**, um die Eigenschaftenseiten zu schließen.  
  
### So fügen Sie eine zusätzliche Berechtigung hinzu, wenn eine Sicherheitsausnahme eintritt  
  
1.  Das Dialogfeld **Ausnahmen\-Assistent** wird mit der folgenden Meldung angezeigt: SecurityException wurde nicht behandelt.  
  
2.  Klicken Sie im Dialogfeld **Ausnahmen\-Assistent** unter **Aktionen** auf **Berechtigung zum Projekt hinzufügen**.  
  
3.  Das Dialogfeld **Debugsitzung neu starten** wird angezeigt.  
  
    -   Wenn Sie die Debugsitzung mit der neuen Berechtigung neu starten möchten, klicken Sie auf **Ja**.  
  
    -   Wenn Sie jetzt nicht neu starten möchten, klicken Sie auf **Nein**.  
  
### So zeigen Sie zusätzliche Berechtigungen an, die beim Debuggen hinzugefügt wurden  
  
1.  Klicken Sie im Menü **Projekt** für *Projectname* auf **Eigenschaften**.  
  
2.  Klicken Sie auf den *Projectname*\-Eigenschaftenseiten auf die Seite **Sicherheit**.  
  
3.  Sehen Sie sich das Datenblatt **Von der Anwendung benötigte Berechtigungen** an.  Für die von Ihnen hinzugefügte zusätzliche Berechtigung sind in der Spalte **Eingeschlossen** zwei Symbole aufgeführt: das normale Häkchen, das alle eingeschlossenen Berechtigungen aufweisen, und ein zusätzliches Symbol, das wie eine Sprechblase mit dem Buchstaben "i" darin aussieht.  
  
4.  Verwenden Sie die vertikale Bildlaufleiste, um das ganze Datenblatt **Von der Anwendung benötigte Berechtigungen** anzuzeigen.  
  
## Siehe auch  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)