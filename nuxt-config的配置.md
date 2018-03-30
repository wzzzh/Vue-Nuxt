# vue-nuxt-nuxt.config.js #
							
	const webpack=require('webpack');
	
	module.exports = {  
	  /*
	  ** Headers of the page  
	  */
					  
	  head: {  
	    title: 'test',   
	    meta: [  
	     //所有meta的配置项
	    ],  
		//fiavicon.ico存放处
	    link: [  
	      { rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }  
	    ]  
	  }, 
	// element-ui需要把module的chalk改成default
	  css: [   
	    'element-ui/lib/theme-default/index.css',  
	    '~assets/css/index.css',  
	  ],  
	  plugins: [
	    '~plugins/element-ui',  
	  ],  
	//配置后打包
	  build: {  
	    vendor: [  
	      'element-ui',  
	      'axios',   
	      'jquery'  
	    ],  
	    plugins: [  
	      new webpack.ProvidePlugin(  
	        {  
	          $: 'jquery',  
	          jQuery: 'jquery',  
	          'window.jQuery': 'jquery'  
	        }  
	      )  
	    ],  
	    babel: {  
	      plugins: [  
	        ['component', [{  
	          libraryName: 'element-ui',  
	          styleLibraryName: 'theme-default'  
	        }]]  
	      ]  
	    },  
	    loaders: [  
	      {  
	        test: /\.(png|jpe?g|gif|svg)$/,  
	        loader: 'url-loader',  
	        query: {  
	          limit: 1000,  
	          name: 'img/[name].[hash:7].[ext]'  
	        }  
	      },  
	      {
	        test: /\.(woff2?|eot|ttf|otf)(\?.*)?$/,  
	        loader: 'url-loader',  
	        query: {  
	          limit: 1000,  
	          name: 'fonts/[name].[hash:7].[ext]'  
	        }  
	      }  
	    ],  
	    postcss: [  
	      require('autoprefixer')({  
	        browsers: ['last 3 versions']  
	      })  
	    ]  
	  },  
	//设置每次切换页面都是默认页面顶部
	  router: {  
	    scrollBehavior: function (to, from, savedPosition) {  
	      return { x: 0, y: 0 }  
	    }  
	  }  
	}  
  

###  postcss.config.js  ###
	module.exports = {
	  plugins: {
	    'autoprefixer': {browsers: 'last 5 version'}
	  }
	}
