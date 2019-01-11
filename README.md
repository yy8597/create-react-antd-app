# create-react-app

##Install

run
`
  npx create-react-app my-app --scripts-version custom-react-scrpits
  cd my-app
  # yarn add react@next react-dom@next #if need hooks
  yarn add antd
`

add `config-overrides.js` in project root
`
  module.exports = {
      webpack: function(config, env) {
          // ...add your webpack config
          return injectBabelPlugin(
              config, 
              ['import', { libraryName: 'antd', libraryDirectory: 'es', style: 'css' }]);
      },
  }
  const find = function(l, fn) {
      return Array.prototype.find.call(l, fn)
  }

  const babelLoader = function(conf) {
    if (!conf.loader) return false;
    return conf.loader.indexOf("babel-loader") > -1;
  };

  const oneOfList = function(conf) {
    if (!conf.oneOf) return false;
    return 1;
  };
  
  const injectBabelPlugin = function(config, pluginName) {
    const babelrc = config.module.rules.find(oneOfList).oneOf.find(babelLoader).options;
    babelrc.plugins = [pluginName].concat(babelrc.plugins || []);
    return config;
  };
`

set `.evn` or add alies in `config-overrides.js`
`
  NODE_PATH=src/
`
