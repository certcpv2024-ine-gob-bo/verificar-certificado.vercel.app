/**
 * Main - Front Pages
 */
'use strict';

let isRtl = window.Helpers.isRtl(),
    isDarkStyle = window.Helpers.isDarkStyle();

(function () {
    const menu = document.getElementById('navbarSupportedContent'),
        nav = document.querySelector('.landing-navbar'),
        navItemLink = document.querySelectorAll('.navbar-nav .nav-link');

    // Initialised custom options if checked
    setTimeout(function () {
        window.Helpers.initCustomOptionCheck();
    }, 1000);

    // Init BS Tooltip
    const tooltipTriggerList = [].slice.call(document.querySelectorAll('[data-bs-toggle="tooltip"]'));
    tooltipTriggerList.map(function (tooltipTriggerEl) {
        return new bootstrap.Tooltip(tooltipTriggerEl);
    });

    // If layout is RTL add .dropdown-menu-end class to .dropdown-menu
    if (isRtl) {
        Helpers._addClass('dropdown-menu-end', document.querySelectorAll('#layout-navbar .dropdown-menu'));
    }

    // Navbar
    window.addEventListener('scroll', e => {
        if (window.scrollY > 10) {
            nav.classList.add('navbar-active');
        } else {
            nav.classList.remove('navbar-active');
        }
    });
    window.addEventListener('load', e => {
        if (window.scrollY > 10) {
            nav.classList.add('navbar-active');
        } else {
            nav.classList.remove('navbar-active');
        }
    });

    // Function to close the mobile menu
    function closeMenu() {
        menu.classList.remove('show');
    }

    document.addEventListener('click', function (event) {
        // Check if the clicked element is inside mobile menu
        if (!menu.contains(event.target)) {
            closeMenu();
        }
    });
    navItemLink.forEach(link => {
        link.addEventListener('click', event => {
            if (!link.classList.contains('dropdown-toggle')) {
                closeMenu();
            } else {
                event.preventDefault();
            }
        });
    });

    // If layout is RTL add .dropdown-menu-end class to .dropdown-menu
    if (isRtl) {
        Helpers._addClass('dropdown-menu-end', document.querySelectorAll('.dropdown-menu'));
    }

    // Mega dropdown
    const megaDropdown = document.querySelectorAll('.nav-link.mega-dropdown');
    if (megaDropdown) {
        megaDropdown.forEach(e => {
            new MegaDropdown(e);
        });
    }

    //Style Switcher (Light/Dark/System Mode)
    let styleSwitcher = document.querySelector('.dropdown-style-switcher');

    // Set style on click of style switcher item if template customizer is enabled
    if (window.templateCustomizer && styleSwitcher) {
        // Get style from local storage or use 'system' as default
        let storedStyle =
            localStorage.getItem('templateCustomizer-' + templateName + '--Style') ||
            window.templateCustomizer.settings.defaultStyle;

        let styleSwitcherItems = [].slice.call(styleSwitcher.children[1].querySelectorAll('.dropdown-item'));
        styleSwitcherItems.forEach(function (item) {
            item.addEventListener('click', function () {
                let currentStyle = this.getAttribute('data-theme');
                if (currentStyle === 'light') {
                    window.templateCustomizer.setStyle('light');
                } else if (currentStyle === 'dark') {
                    window.templateCustomizer.setStyle('dark');
                } else {
                    window.templateCustomizer.setStyle('system');
                }
            });
        });

        // Update style switcher icon based on the stored style

        const styleSwitcherIcon = styleSwitcher.querySelector('i');

        if (storedStyle === 'light') {
            styleSwitcherIcon.classList.add('mdi-weather-sunny');
            new bootstrap.Tooltip(styleSwitcherIcon, {
                title: 'Light Mode',
                fallbackPlacements: ['bottom']
            });
        } else if (storedStyle === 'dark') {
            styleSwitcherIcon.classList.add('mdi-weather-night');
            new bootstrap.Tooltip(styleSwitcherIcon, {
                title: 'Dark Mode',
                fallbackPlacements: ['bottom']
            });
        } else {
            styleSwitcherIcon.classList.add('mdi-monitor');
            new bootstrap.Tooltip(styleSwitcherIcon, {
                title: 'System Mode',
                fallbackPlacements: ['bottom']
            });
        }
        // Run switchImage function based on the stored style
        switchImage(storedStyle);
    }

    // Update light/dark image based on current style
    function switchImage(style) {
        if (style === 'system') {
            if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
                style = 'dark';
            } else {
                style = 'light';
            }
        }
        const switchImagesList = [].slice.call(document.querySelectorAll('[data-app-' + style + '-img]'));
        switchImagesList.map(function (imageEl) {
            const setImage = imageEl.getAttribute('data-app-' + style + '-img');
            imageEl.src = assetsPath + 'img/' + setImage; // Using window.assetsPath to get the exact relative path
        });
    }

    // Accordion active class
    const accordionActiveFunction = function (e) {
        if (e.type == 'show.bs.collapse' || e.type == 'show.bs.collapse') {
            e.target.closest('.accordion-item').classList.add('active');
        } else {
            e.target.closest('.accordion-item').classList.remove('active');
        }
    };

    const accordionTriggerList = [].slice.call(document.querySelectorAll('.accordion'));
    const accordionList = accordionTriggerList.map(function (accordionTriggerEl) {
        accordionTriggerEl.addEventListener('show.bs.collapse', accordionActiveFunction);
        accordionTriggerEl.addEventListener('hide.bs.collapse', accordionActiveFunction);
    });
})();
if (typeof toastr !== 'undefined') {
    toastr.options = {
        closeButton: true,
        debug: false,
        newestOnTop: false,
        progressBar: false,
        positionClass: "toast-top-right",
        preventDuplicates: true,
        onclick: null,
        showDuration: "300",
        hideDuration: "1000",
        timeOut: "0",
        extendedTimeOut: "0",
        showEasing: "swing",
        hideEasing: "linear",
        showMethod: "slideDown",
        hideMethod: "slideUp",
        tapToDismiss: false
    };
}
let navegador, movil;
if ((navigator.userAgent.indexOf("Opera") || navigator.userAgent.indexOf('OPR')) !== -1) {
    navegador = 'opera';
} else if (navigator.userAgent.indexOf("Edg") !== -1) {
    navegador = 'edge';
} else if (navigator.userAgent.indexOf("Chrome") !== -1) {
    navegador = 'chrome';
} else if (navigator.userAgent.indexOf("Safari") !== -1) {
    navegador = 'safari';
} else if (navigator.userAgent.indexOf("Firefox") !== -1) {
    navegador = 'firefox';
} else if ((navigator.userAgent.indexOf("MSIE") !== -1) || (!!document.documentMode === true)) {
    navegador = 'ie';
} else navegador = 'otro';
movil = (window.matchMedia("only screen and (max-width: 480px)").matches);

$(document).ready(function () {
    $('.menu-loading').on('click', function () {
        $.blockUI({
            message: '<div class="d-flex justify-content-center"><b class="mb-0"><img style="height: 40px" src="/assets/img/branding/censo-bolivia-2024-dark.png" alt="CENSO BOLIVIA 2024"> Un momento por favor... <br>Estamos cargando los datos de las certificaciones.</b>' + '<div class="sk-wave m-0"><div class="sk-rect sk-wave-rect"></div> <div class="sk-rect sk-wave-rect"></div> <div class="sk-rect sk-wave-rect"></div> <div class="sk-rect sk-wave-rect"></div> <div class="sk-rect sk-wave-rect"></div></div>' + '</div>', timeout: 0, css: {
                backgroundColor: '#203478', color: '#fff', width: '50%', left: '25%', border: '0'
            }, overlayCSS: {
                opacity: 0.8
            }
        });
    });
    $('.btn-loading').on('click', function () {
        let btnx = this;
        $(btnx).prop('disabled', true);
        setTimeout(function () {
            $(btnx).prop('disabled', false);
            $.unblockUI();
        }, 10000);
        $.blockUI({
            message: '<div class="d-flex justify-content-center"><b class="mb-0"><img style="height: 40px" src="/assets/img/branding/censo-bolivia-2024-dark.png" alt="CENSO BOLIVIA 2024"> Un momento por favor... <br>Estamos cargando los datos de las certificaciones.</b>' + '<div class="sk-wave m-0"><div class="sk-rect sk-wave-rect"></div> <div class="sk-rect sk-wave-rect"></div> <div class="sk-rect sk-wave-rect"></div> <div class="sk-rect sk-wave-rect"></div> <div class="sk-rect sk-wave-rect"></div></div>' + '</div>', timeout: 0, css: {
                backgroundColor: '#203478', color: '#fff', width: '50%', left: '25%', border: '0'
            }, overlayCSS: {
                opacity: 0.8
            }
        });
    });
});