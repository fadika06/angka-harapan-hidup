# angka-harapan-hidup
 Angka Harapan Hidup (AHH) Menurut Kabupaten/Kota Se-Provinsi
 
### install via composer

- Development snapshot
```bash
$ composer require bantenprov/angka-harapan-hidup:dev-master
```
- Latest release:


### download via github

~~~bash
$ git clone https://github.com/bantenprov/bantenprov/angka-harapan-hidup.git
~~~


#### Edit `config/app.php` :
```php

'providers' => [

    /*
    * Laravel Framework Service Providers...
    */
    Illuminate\Auth\AuthServiceProvider::class,
    Illuminate\Broadcasting\BroadcastServiceProvider::class,
    Illuminate\Bus\BusServiceProvider::class,
    Illuminate\Cache\CacheServiceProvider::class,
    Illuminate\Foundation\Providers\ConsoleSupportServiceProvider::class,
    Illuminate\Cookie\CookieServiceProvider::class,
    
    //....
    Bantenprov\AngkaHarapanHidup\AngkaHarapanHidupServiceProvider::class,

```

#### Tambahkan route di dalam route : `resources/assets/js/routes.js` :

```javascript
path: '/dashboard',
component: layout('Default'),
children: [
  {
    path: '/dashboard',
    components: {
      main: resolve => require(['./components/views/DashboardHome.vue'], resolve),
      navbar: resolve => require(['./components/Navbar.vue'], resolve),
      sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
    },
    meta: {
      title: "Dashboard"
    }
  },
  //== ...
  {
    path: '/dashboard/angka-harapan-hidup',
    components: {
      main: resolve => require(['./components/views/bantenprov/angka-harapan-hidup/DashboardAngkaHarapanHidup.vue'], resolve),
      navbar: resolve => require(['./components/Navbar.vue'], resolve),
      sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
    },
    meta: {
      title: "Angka Harapan Hidup"
    }
  }
```

```javascript
{
path: '/admin',
redirect: '/admin/dashboard',
component: resolve => require(['./AdminLayout.vue'], resolve),
children: [
//== ...
    {
      path: '/admin/dashboard/angka-harapan-hidup',
      components: {
        main: resolve => require(['./components/bantenprov/angka-harapan-hidup/AngkaHarapanHidupAdmin.view.vue'], resolve),
        navbar: resolve => require(['./components/Navbar.vue'], resolve),
        sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
      },
      meta: {
        title: "Angka Harapan Hidup"
      }
    }
 //== ...   
  ]
},

```

#### Edit menu `resources/assets/js/menu.js`

```javascript
{
  name: 'Dashboard',
  icon: 'fa fa-dashboard',
  childType: 'collapse',
  childItem: [
    {
      name: 'Dashboard',
      link: '/dashboard',
      icon: 'fa fa-angle-double-right'
    },
    {
      name: 'Entity',
      link: '/dashboard/entity',
      icon: 'fa fa-angle-double-right'
    },
    //== ...
    {
      name: 'Angka Harapan Hidup',
      link: '/admin/dashboard/angka-harapan-hidup',
      icon: 'fa fa-angle-right'
    }
  ]
},
{
  name: 'Admin',
  icon: 'fa fa-lock',
  childType: 'collapse',
  childItem: [
    {
      name: 'Dashboard',
      icon: 'fa fa-angle-double-right',
      child: [
        {
          name: 'Home',
          link: '/admin/dashboard/home',
          icon: 'fa fa-angle-right'
        },
        //== ...
        {
          name: 'Angka Harapan Hidup',
          link: '/admin/dashboard/angka-harapan-hidup',
          icon: 'fa fa-angle-right'
        }
      ]
    },
  ]
}
```


#### Tambahkan components `resources/assets/js/components.js` :

```javascript

//== Angka Harapan Hidup
import AngkaHarapanHidup from './components/bantenprov/angka-harapan-hidup/AngkaHarapanHidup.chart.vue';
Vue.component('echarts-angka-harapan-hidup', AngkaHarapanHidup);

import AngkaHarapanHidupKota from './components/bantenprov/angka-harapan-hidup/AngkaHarapanHidupKota.chart.vue';
Vue.component('echarts-angka-harapan-hidup-kota', AngkaHarapanHidupKota);

import AngkaHarapanHidupTahun from './components/bantenprov/angka-harapan-hidup/AngkaHarapanHidupTahun.chart.vue';
Vue.component('echarts-angka-harapan-hidup-tahun', AngkaHarapanHidupTahun);

import AngkaHarapanHidupBar01 from './components/views/bantenprov/angka-harapan-hidup/AngkaHarapanHidupBar01.vue';
Vue.component('angka-harapan-hidup-bar-01', AngkaHarapanHidupBar01);

import AngkaHarapanHidupBar02 from './components/views/bantenprov/angka-harapan-hidup/AngkaHarapanHidupBar02.vue';
Vue.component('angka-harapan-hidup-bar-02', AngkaHarapanHidupBar02);

import AngkaHarapanHidupBar03 from './components/views/bantenprov/angka-harapan-hidup/AngkaHarapanHidupBar03.vue';
Vue.component('angka-harapan-hidup-bar-03', AngkaHarapanHidupBar03);

import AngkaHarapanHidupPie01 from './components/views/bantenprov/angka-harapan-hidup/AngkaHarapanHidupPie01.vue';
Vue.component('angka-harapan-hidup-pie-01', AngkaHarapanHidupPie01);

import AngkaHarapanHidupPie02 from './components/views/bantenprov/angka-harapan-hidup/AngkaHarapanHidupPie02.vue';
Vue.component('angka-harapan-hidup-pie-02', AngkaHarapanHidupPie02);

import AngkaHarapanHidupPie03 from './components/views/bantenprov/angka-harapan-hidup/AngkaHarapanHidupPie03.vue';
Vue.component('angka-harapan-hidup-pie-03', AngkaHarapanHidupPie03);
```

#### Untuk publish component vue :

```bash
$ php artisan vendor:publish --tag=angka-harapan-hidup-assets
```


