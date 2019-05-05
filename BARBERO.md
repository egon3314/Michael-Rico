      // Michael Rico Morales
      // Unipanamericana
      // Sistemas Operativos 
      // El Barbero Dormilon

Clientes_Semaforo = 0; 
Semaforo_Barbero = 0; 
Asientos_disponibles = 1; 
int AsientosLibres = N; 
 
Barbero { 
        while ( true ) { 
        
          // El barbero espera un cliente (standby)

down(Cliente); 
 
             // Bloqueo que protege el número de asientos disponibles
down(Asiento); 
 
             // Se libera una silla 
             
AsientoLibre++; 
            
             // Llamar cliente para corte de pelo 
             
up(Barbero); 
            
             // Se desbloquea el Asiento
             
up(Asiento);

            // El barbero corta el pelo
            
  } 
 } 
 
 Cliente { 
        while ( true ) {    
        
           // Bloquea los asientos para que solo un cliente pueda sentarse en un asiento si aplica 
                 
down(Asiento);
              if (AsientoLibre > 0) 
              { 
                  
                   // Sentado 
AsientoLibre--; 
                  
                   // Notificar al Barbero 
up(Cliente); 
                  
                   // Se libera el bloqueo 
up(Asiento); 
                  
                   // Espera en la sala de espera si el barbero esta ocupado 
down(Barbero);                                                                                                                                              // El cliente se encuentra en corte de pelo 
} else 
      
  { 
                   // Se libera el bloqueo 
up(Asiento); 

                   // El cliente termina su servicio y se retira de la barberia. 
 } 
    } 
 } 
