---
title: "Empfohlene Vorgehensweisen bez&#252;glich der Sicherheit in Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sicherheit [Visual Studio SDK]"
  - "Benutzerkontensteuerung [Visual Studio SDK]"
  - "Visual Studio SDK, Sicherheit"
  - "UAC (User Account Control, Benutzerkontensteuerung) [Visual Studio SDK]"
  - "Empfohlene Vorgehensweisen bezüglich der Sicherheit, Visual Studio SDK"
  - "Windows Vista, Benutzerkontensteuerung [Visual Studio SDK]"
ms.assetid: 56c8a113-0c53-4969-a009-a2ab58d855c3
caps.latest.revision: 30
caps.handback.revision: 30
manager: "douge"
---
# Empfohlene Vorgehensweisen bez&#252;glich der Sicherheit in Visual Studio SDK
Sie müssen die Sicherheit für VSPackage\-Erweiterungen verstehen, sodass Sie die bestmöglichen Produkte erstellen können.  
  
 Mit einem sicheren Produkt lässt sich Folgendes schützen:  
  
-   Vertraulichkeit, Integrität und Verfügbarkeit der Informationen eines Kunden  
  
-   Integrität und Verfügbarkeit der Verarbeitungsressourcen unter der Kontrolle des Systembesitzers oder \-administrators  
  
## Sicherheitsrisiko  
 Ein Sicherheitsrisiko ist eine Schwachstelle in einem Produkt, die es unmöglich macht, böswillige Aktivitäten ein Angreifers zu verhindern, und zwar selbst dann, wenn das Produkt ordnungsgemäß verwendet wird. Hier einige Beispiele:  
  
-   Erlangen von Berechtigungen auf einem Computer, die höher sind als die des Benutzers  
  
-   Übernehmen der Bedienung des Computer eines Benutzers  
  
-   Beschädigen von Daten auf dem Computer eines Benutzers  
  
> [!IMPORTANT]
>  Gehen Sie nicht davon aus, dass Ihre Anwendung nur in bestimmten Umgebungen ausgeführt wird. Ihre Anwendung wird möglicherweise in Zusammenhängen verwendet, die Sie nicht erwartet haben, insbesondere wenn die Anwendung populär wird. Gehen Sie stattdessen davon aus, dass Ihr Code in feindlichen Umgebungen ausgeführt wird, und entwerfen, schreiben und testen Sie Ihren Code entsprechend.  
  
 Produkte und Systeme, die mit dem Aspekt Sicherheit als einem wesentlichen Merkmal entworfen und erstellt wurden, sind robuster als solche, für die Sicherheit beim Schreiben nachrangig war. Sichere Produkte sind zudem weniger anfällig für Medienkritik, attraktiver für Benutzer und preiswerter in Bezug auf Support und Upgrade.  
  
## Gefährliche APIs  
 Aufrufe einiger Funktionen können unerwünschte Sicherheitsrisiken erzeugen, wenn sie nicht ordnungsgemäß verwendet werden, ein Verbieten ihrer Verwendung führt aber nicht notwendigerweise zu sicherem Code. Dennoch wurden für einige Softwareprojekte messbare Zuwächse hinsichtlich der Sicherheit erzielt, indem Funktionen verboten wurden, die kaum sicher zu verwenden sind \(dies als eine der vielen sicherheitsbezogenen Entwicklungsverfahren\). Weitere Informationen hierzu finden Sie im Anhang A des Microsoft Press\-Buchs „Sichere Software programmieren“ von Michael Howard und David LeBlanc.  
  
 Die meisten Sicherheitsprobleme ergeben sich dadurch, dass einer Eingabe vertraut wird, ohne diese angemessen zu überprüfen. Gehen Sie unbedingt so vor, dass Sie Daten verfolgen, nachdem sie in Ihren Code gelangt sind, und hinterfragen Sie die Auswirkungen von Vorgängen mit diesen Daten. Sie können sicheren Code mit fast allen Funktionen schreiben, wenn die Dateneingaben wohlgeformt sind und auf Vertrauenswürdigkeit überprüft werden.  
  
## Probleme mit der Benutzerkontensteuerung \(UAC\)  
 Die Benutzerkontensteuerung \(User Account Control, UAC\) hat Sicherheitsauswirkungen, die Sie kennen sollten. Sie verringert die Angriffsfläche, die das Betriebssystem und Anwendungen böswilligen Angriffen bieten.  
  
1.  Weitere Informationen zur Benutzerkontensteuerung unter [!INCLUDE[win7](../debugger/includes/win7_md.md)] finden Sie unter [Was ist die Benutzerkontensteuerung?](http://go.microsoft.com/fwlink/?linkid=159927).  
  
2.  Weitere Informationen zur Benutzerkontensteuerung unter [!INCLUDE[win8](../debugger/includes/win8_md.md)] finden Sie unter [Was sind Einstellungen zur Benutzerkontensteuerung?](http://windows.microsoft.com/windows-8/what-are-uac-settings).  
  
 Vor der Einführung von UAC haben Entwickler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in der Regel unter Administratorberechtigungen ausgeführt, selbst wenn diese nicht erforderlich waren. Sie sollten die Entwicklung und das Testen Ihrer Erweiterung als normaler Benutzer vornehmen, damit Sie sicherstellen können, dass die Erweiterung nicht unnötigerweise erhöhte Rechte erfordert.  
  
 Beachten Sie, dass sich UAC auch auf eine Bereitstellung auswirkt. Installationspakete müssen ordnungsgemäß geschrieben werden, damit sie UAC unterstützen. Ein nicht ordnungsgemäß geschriebenes Paket verursacht typischerweise „Zugriff verweigert“\-Fehler, weil das Installationsprogramm versucht, normale Benutzerrechte zu verwenden, um eine Aufgabe auszuführen, für die erhöhte Rechte erforderlich sind.  
  
## Siehe auch  
 [Best Practices für die Sicherheit in VSPackages](../extensibility/internals/best-practices-for-security-in-vspackages.md)   
 [Ressourcen für das Erstellen sicherer Anwendungen](http://msdn.microsoft.com/de-de/0ebf5f69-76f2-498a-a2df-83cf3443e132)   
 [Key Security Concepts](../Topic/Key%20Security%20Concepts.md)