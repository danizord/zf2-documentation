.. EN-Revision: none
.. _zend.mail.different-transports:

Použitie rôznych spôsobov prenosu
=================================

V prípade, že je potrebné poslať e-mail cez iné pripojenie je možné nastaviť spôsob prenosu priamo pri
volaní *send()* bez volania *setDefaultTransport()*. Predaný spôsob prenosu sa použije na miesto
prednastaveného pre aktuálne volanie *send()*:

.. rubric:: Použitie rôznych spôsobov prenosu

.. code-block:: php
   :linenos:

   <?php
   require_once 'Zend/Mail.php';
   $mail = new Zend\Mail\Mail();
   // vytvorenie správy...
   require_once 'Zend/Mail/Transport/Smtp.php';
   $tr1 = new Zend\Mail_Transport\Smtp('server@example.com');
   $tr2 = new Zend\Mail_Transport\Smtp('other_server@example.com');
   $mail->send($tr1);
   $mail->send($tr2);
   $mail->send();  // použije sa prednastavený
   ?>
.. note::

   **Iné spôsoby prenosu**

   Ostatné spôsoby prenosu môžu byt vytvorené implementáciou *Zend\Mail_Transport\Interface*.


