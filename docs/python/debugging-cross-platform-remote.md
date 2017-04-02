---
title: "Plattformübergreifendes Remotedebuggen mit Python Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 7634da4bdc2b0186f410acb4eaf57a70ddea3e91
ms.lasthandoff: 03/10/2017

---

# <a name="remotely-debugging-python-code"></a>Remotedebuggen von Python-Code

Python Tools für Visual Studio (PTVS) kann Python-Anwendungen sowohl lokal als auch remote (siehe [Remotedebuggen](../debugger/remote-debugging.md)) auf einem Windows-Computer starten und debuggen. Mithilfe der [ptvsd-Bibliothek](https://pypi.python.org/pypi/ptvsd) kann PTVS das Remotedebuggen auch auf einem anderen Betriebssystem, einem anderen Gerät oder in einer anderen Python-Implementierung als CPython ausführen.

Beim Verwenden von ptvsd hostet der Python-Code, für den das Debuggen ausgeführt werden soll, den Debugserver, an den Visual Studio angefügt werden kann. Dafür ist eine kleine Änderung an Ihrem Code erforderlich, um den Server zu importieren und zu aktivieren. Auf dem Remotecomputer müssen möglicherweise Netzwerk- oder Firewallkonfigurationen geändert werden, sodass TCP-Verbindungen zulässig sind.

Eine Einführung zum Remotedebuggen sehen Sie in diesem Video: [Deep Dive: Cross-Platform Remote Debugging](https://youtu.be/y1Qq7BrV6Cc) (youtube.com, 6 Minuten, 22 Sekunden).

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="preparing-the-script-for-debugging"></a>Vorbereiten des Skripts für das Debuggen

1. Erstellen Sie eine Python-Datei mit dem folgenden Code auf dem Remotecomputer:

  ```python
  import random

  guesses_made = 0
  name = raw_input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print 'Well, {0}, I am thinking of a number between 1 and 20.'.format(name)

  while guesses_made < 6:
      guess = int(raw_input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print 'Your guess is too low.'
      if guess > number:
          print 'Your guess is too high.'
      if guess == number:
          break
  if guess == number:
      print 'Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made)
  else:
      print 'Nope. The number I was thinking of was {0}'.format(number)
  ```
 
1. Installieren Sie mithilfe von `pip install ptvsd` das `ptvsd`-Paket in Ihrer Umgebung.

1. Aktivieren Sie das Remotedebuggen, indem Sie den unten stehenden Code am frühestmöglichen Punkt im Skript einfügen, also vor jedem anderen Code. (Dies ist zwar nicht zwingend erforderlich, aber es ist unmöglich, Hintergrundthreads zu debuggen, die vor dem Aufruf der Funktion `enable_attach` erzeugt werden.)

   ```python
   import ptvsd
   ptvsd.enable_attach(secret='my_secret')
   ```

   Der an `enable_attach` übergebene `secret`-Parameter wird verwendet, um den Zugriff auf die Skriptausführung zu beschränken. Beim Anfügen müssen Sie den Parameter in Visual Studio angeben, da die Verbindung sonst abgelehnt wird. Um dieses Verhalten zu deaktivieren und jedem Benutzer das Herstellen einer Verbindung zu ermöglichen, verwenden Sie `enable_attach(secret=None)`.

1. Speichern Sie die Datei, und starten Sie das Skript auf dem Remotecomputer. Beachten Sie, dass der Aufruf von `enable_attach` im Hintergrund ausgeführt wird und auf eingehende Verbindungen wartet. Bei Bedarf kann die Funktion `wait_for_attach` nach `enable_attach` aufgerufen werden, um das Programm zu blockieren, bis der Debugger angefügt wurde.

Zusätzlich zu `enable_attach` und `wait_for_attach` bietet ptvsd auch die Hilfsfunktion `break_into_debugger`, die als programmgesteuerter Haltepunkt fungiert, wenn der Debugger angefügt wird. Es gibt auch eine `is_attached`-Funktion, die `True` zurückgibt, wenn der Debugger angefügt wird (das Ergebnis muss vor dem Aufrufen anderer `ptvsd`-Funktionen nicht geprüft werden).

## <a name="attaching-remotely-from-python-tools"></a>Remoteanfügen über Python Tools

In diesen Schritten legen wir einen einfachen Haltepunkt fest, um den Remoteprozess anzuhalten.

1. Erstellen Sie eine Kopie der Remotedatei auf dem lokalen Computer, und öffnen Sie diese in Visual Studio. Es spielt keine Rolle, wo die Datei gespeichert wird, der Name muss aber dem Namen des Skripts auf dem Remotecomputer entsprechen, für den das Anfügen erfolgen soll.

1. Wählen Sie **Debuggen > An den Prozess anhängen**, um das Dialogfeld „An den Prozess anhängen“ zu öffnen.

1. Legen Sie **Transport** auf **Python-Remotedebuggen** fest.

1. Geben Sie die Adresse des Remotecomputers in das Feld **Qualifizierer** ein, und drücken Sie die EINGABETASTE. Dadurch werden verfügbare Prozesse auf diesem Computer aufgelistet:

![Eingeben des Qualifizierers und Auflisten von Prozessen](media/remote-debugging-qualifier.png)

1. Ein Fehler in dieser Phase weist in der Regel darauf hin, dass die Geheimnisse nicht übereinstimmten, die `ptvsd`-Version nicht der von PTVS verwendeten Version entspricht oder keine Verbindung hergestellt werden konnte. Eine der häufigsten Ursachen für Verbindungsfehler ist eine Firewall auf dem Remotecomputer, die den Port des Debugservers blockiert (Standardwert: 5678). Sie können die Firewall neu konfigurieren oder einen anderen Port verwenden. Um einen anderen Port anzugeben, legen Sie den Port explizit im Aufruf von `enable_attach` im Parameter `address` fest. Beispiel:

  ```python
  ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))
  ```

  Das Adressformat ist das gleiche wie beim standardmäßigen Python-Modulsocket für Sockets des Typs `AF_INET`. Informationen finden Sie in der zugehörigen [Dokumentation](http://docs.python.org/3/library/socket.html#socket-families). 

1. Sobald der Prozess in der Liste angezeigt wird, doppelklicken Sie darauf, um ihn anzufügen. Visual Studio öffnet die Debuggingtools, während das Skript weiter ausgeführt wird. Wenn Sie z.B. in das oben gezeigte Skript eine Zahl eingeben, führt dies dazu, dass der Haltepunkt erreicht wird:

    ![Haltepunkt wird erreicht](media/remote-debugging-breakpoint-hit.png)

1. An diesem Punkt können Sie alle üblichen PTVS-Debugfunktionen verwenden. 

1. Wenn das Debuggen abgeschlossen ist, wird Visual Studio von Ihrem Skript getrennt, aber das Skript wird weiter auf dem Remotecomputer ausgeführt. Der Debugserver wird im Hintergrundthread ebenfalls weiter ausgeführt, sodass Sie Visual Studio später mit dem gleichen Verfahren erneut an den Prozess anfügen können.


## <a name="securing-the-debugger-connection-with-ssl"></a>Sichern der Debuggerverbindung mit SSL

Standardmäßig ist die Verbindung mit dem PTVS-Remotedebugserver in keiner Weise geschützt. Jeder Benutzer, der über das Geheimnis verfügt, kann eine Verbindung herstellen, und alle Daten werden als Nur-Text übergeben. Daher können andere Netzwerkbenutzer die Daten ausspähen oder sogar einen Man-In-The-Middle-Angriff (MITM) ausführen. Um diese Sicherheitslücken beim Debuggen über nicht gesicherte Netzwerke oder das Internet zu schließen, unterstützt der Debugserver SSL. 

Um den Kanal mit SSL zu sichern, benötigen Sie ein SSL-Zertifikat. Sie können selbst ein selbstsigniertes Zertifikat generieren, wie in der [Dokumentation für das Python-Standardmodul`ssl`](http://docs.python.org/3/library/ssl.html#self-signed-certificates) beschrieben. Um MITM-Angriffe zu verhindern, muss ein solches generiertes Zertifikat auch zum Stammspeicher der Zertifizierungsstelle auf dem Windows-Computer hinzugefügt werden, auf dem PTVS ausgeführt wird. Hierzu können Sie den Zertifikat-Manager (certmgr.msc) verwenden, wie unter [How do I export certificates and/or private keys?](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/how-do-i-export-certificates-andor-private-keys/7722900a-e848-4076-bc50-9e2f5e3c66ac) (Wie exportiere ich Zertifikate und/oder private Schlüssel?) beschrieben. Beachten Sie, dass Sie für den Import über eine separate Zertifikatsdatei verfügen müssen (nicht mit dem privaten Schlüssel in einer einzigen Datei kombiniert). 

Nachdem Sie das Zertifikat und die privaten Schlüsseldateien generiert und registriert haben, müssen Sie den Aufruf von `enable_attach` in Ihrem Skript aktualisieren, damit diese Dateien verwendet werden. Hierzu verwenden Sie die Parameter `certfile` und `keyfile`, die die gleiche Bedeutung haben wie die Python-Standardfunktion `ssl.wrap_socket`. Ein Beispiel: Wenn die Zertifikatdatei `my_cert.cer` und die Schlüsseldatei `my_cert.key` heißt, verwenden Sie folgenden Code: 

```python
ptvsd.enable_attach(secret='my_secret', certfile='my_cert.cer', keyfile='my_cert.key')
```

Der Anfügungsprozess ist der gleiche wie oben beschrieben, mit einer Ausnahme: Sie verwenden nicht das `tcp://`-Schema im Qualifizierer, sondern `tcps://`: 

![Auswählen des Transports für das Remotedebuggen über SSL](media/remote-debugging-qualifier-ssl.png)

Wenn Sie dem Stammspeicher der Zertifizierungsstelle kein Zertifikat hinzugefügt haben, wird eine Warnmeldung angezeigt: 

![SSL-Zertifikatwarnung](media/remote-debugging-ssl-warning.png)

Sie können diese Warnung ignorieren und mit dem Debuggen fortfahren. Der Kanal wird dann zwar gegen mögliche Lauscher verschlüsselt, die Gefahr eines MITM-Angriffs besteht aber weiterhin.

