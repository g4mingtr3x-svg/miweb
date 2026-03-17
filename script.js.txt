// script.js - Interactividad para la landing page DentalAI

document.addEventListener('DOMContentLoaded', function() {
  console.log('🚀 Landing page DentalAI cargada correctamente');

  // Elementos del DOM
  const demoButton = document.getElementById('demoButton');
  const startButton = document.getElementById('startButton');
  const watchButton = document.getElementById('watchButton');
  const crmButton = document.getElementById('crmButton');
  const adsButton = document.getElementById('adsButton');
  const ctaButton = document.getElementById('ctaButton');
  
  // Elementos visuales para efectos
  const heroImage = document.getElementById('heroImage');
  const featureCards = document.querySelectorAll('.feature-card');
  const crmImage = document.getElementById('crmImage');
  const adsImage = document.getElementById('adsImage');
  const galleryItems = document.querySelectorAll('.gallery-item');

  // Función para mostrar notificaciones simuladas
  function showNotification(message, icon = '🤖') {
    // Crear elemento de notificación
    const notification = document.createElement('div');
    notification.style.position = 'fixed';
    notification.style.bottom = '20px';
    notification.style.right = '20px';
    notification.style.backgroundColor = '#0b2b40';
    notification.style.color = 'white';
    notification.style.padding = '16px 24px';
    notification.style.borderRadius = '50px';
    notification.style.boxShadow = '0 10px 30px rgba(0,0,0,0.2)';
    notification.style.zIndex = '9999';
    notification.style.display = 'flex';
    notification.style.alignItems = 'center';
    notification.style.gap = '12px';
    notification.style.fontWeight = '500';
    notification.style.animation = 'slideIn 0.3s ease';
    notification.innerHTML = `<span style="font-size: 1.5rem;">${icon}</span> <span>${message}</span>`;
    
    // Añadir animación
    const style = document.createElement('style');
    style.textContent = `
      @keyframes slideIn {
        from { transform: translateX(100px); opacity: 0; }
        to { transform: translateX(0); opacity: 1; }
      }
    `;
    document.head.appendChild(style);
    
    document.body.appendChild(notification);
    
    // Eliminar después de 3 segundos
    setTimeout(() => {
      notification.style.animation = 'slideIn 0.3s reverse';
      setTimeout(() => {
        document.body.removeChild(notification);
      }, 300);
    }, 3000);
  }

  // Event listeners para botones
  if (demoButton) {
    demoButton.addEventListener('click', function() {
      showNotification('📅 Demo solicitada - Te contactaremos en 5 min', '📞');
    });
  }

  if (startButton) {
    startButton.addEventListener('click', function() {
      showNotification('⚡ Iniciando automatización... ¡Bienvenido!', '🚀');
    });
  }

  if (watchButton) {
    watchButton.addEventListener('click', function() {
      showNotification('🎥 Video demostrativo - Abriendo reproductor', '▶️');
    });
  }

  if (crmButton) {
    crmButton.addEventListener('click', function() {
      showNotification('📊 Accediendo al CRM demo (simulación)', '📋');
    });
  }

  if (adsButton) {
    adsButton.addEventListener('click', function() {
      showNotification('📢 Activando campaña Meta AI con presupuesto diario de 10€', '💰');
    });
  }

  if (ctaButton) {
    ctaButton.addEventListener('click', function() {
      showNotification('📆 Redirigiendo al calendario de citas con expertos', '🗓️');
    });
  }

  // Efecto hover mejorado en las imágenes
  if (heroImage) {
    heroImage.addEventListener('mouseenter', function() {
      this.style.transform = 'scale(1.02)';
      this.style.transition = 'transform 0.3s ease';
    });
    heroImage.addEventListener('mouseleave', function() {
      this.style.transform = 'scale(1)';
    });
  }

  if (crmImage) {
    crmImage.addEventListener('mouseenter', function() {
      this.style.transform = 'scale(1.02)';
      this.style.transition = 'transform 0.3s ease';
    });
    crmImage.addEventListener('mouseleave', function() {
      this.style.transform = 'scale(1)';
    });
  }

  if (adsImage) {
    adsImage.addEventListener('mouseenter', function() {
      this.style.transform = 'scale(1.02)';
      this.style.transition = 'transform 0.3s ease';
    });
    adsImage.addEventListener('mouseleave', function() {
      this.style.transform = 'scale(1)';
    });
  }

  // Efecto en las tarjetas de características
  featureCards.forEach((card, index) => {
    card.addEventListener('click', function() {
      const features = [
        'mensajes automáticos',
        'gestión de citas',
        'publicidad Meta AI',
        'CRM completo'
      ];
      showNotification(`🔧 Probando funcionalidad: ${features[index]}`, '✨');
    });
    
    // Efecto de entrada secuencial
    setTimeout(() => {
      card.style.opacity = '1';
      card.style.transform = 'translateY(0)';
    }, 200 * index);
  });

  // Inicializar opacidad para animación de entrada
  featureCards.forEach(card => {
    card.style.opacity = '0';
    card.style.transform = 'translateY(20px)';
    card.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
  });

  // Forzar el cálculo de estilos para que la animación se ejecute
  setTimeout(() => {
    featureCards.forEach(card => {
      card.style.opacity = '1';
      card.style.transform = 'translateY(0)';
    });
  }, 100);

  // Efecto de parallax simple en la galería
  window.addEventListener('scroll', function() {
    const scrollPosition = window.scrollY;
    
    galleryItems.forEach((item, index) => {
      const speed = 0.05 * (index + 1);
      const yPos = -(scrollPosition * speed);
      item.style.backgroundPosition = `center ${yPos}px`;
    });
  });

  // Contador animado para las estadísticas del CRM (efecto visual)
  const crmStats = document.querySelectorAll('.crm-stats span');
  if (crmStats.length > 0) {
    // Detectar cuando la sección es visible
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          // Animar el contador de +2.400
          const statElement = crmStats[0];
          if (statElement && statElement.innerText.includes('2.400')) {
            let count = 2100;
            const target = 2400;
            const interval = setInterval(() => {
              count += 15;
              if (count >= target) {
                statElement.innerText = '+2.400';
                clearInterval(interval);
              } else {
                statElement.innerText = '+' + count;
              }
            }, 20);
          }
          
          // Animar el 98%
          const statElement2 = crmStats[1];
          if (statElement2 && statElement2.innerText.includes('98')) {
            let count = 92;
            const target = 98;
            const interval = setInterval(() => {
              count += 1;
              if (count >= target) {
                statElement2.innerText = '98%';
                clearInterval(interval);
              } else {
                statElement2.innerText = count + '%';
              }
            }, 50);
          }
          
          observer.disconnect(); // Solo una vez
        }
      });
    }, { threshold: 0.5 });
    
    const crmSection = document.querySelector('.crm-preview');
    if (crmSection) {
      observer.observe(crmSection);
    }
  }

  // Efecto de escritura automática en el hero (opcional)
  const heroSpan = document.querySelector('.hero-image span');
  if (heroSpan) {
    const originalText = heroSpan.innerText;
    let canAnimate = true;
    
    heroImage.addEventListener('mouseenter', function() {
      if (!canAnimate) return;
      
      heroSpan.style.transition = 'opacity 0.3s';
      heroSpan.style.opacity = '0';
      
      setTimeout(() => {
        heroSpan.innerText = '🦷 Prueba gratuita disponible';
        heroSpan.style.opacity = '1';
      }, 300);
      
      setTimeout(() => {
        heroSpan.style.opacity = '0';
        setTimeout(() => {
          heroSpan.innerText = originalText;
          heroSpan.style.opacity = '1';
        }, 300);
      }, 2000);
      
      canAnimate = false;
      setTimeout(() => { canAnimate = true; }, 4000);
    });
  }

  console.log('✅ Todos los eventos han sido inicializados');
});