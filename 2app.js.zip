const express = require('express');
const path = require('path');
const hbs = require('hbs');

const app = express();

// Set view engine
app.set('view engine', 'hbs');
app.set('views', path.join(__dirname, 'app_server', 'views'));

// Register partials
hbs.registerPartials(path.join(__dirname, 'app_server', 'views', 'partials'));

// Static files
app.use(express.static(path.join(__dirname, 'public')));

// Routes
const indexRouter = require('./app_server/routes/index');
app.use('/', indexRouter);

// Port
const port = 3000;
app.listen(port, () => {
    console.log(`App running on http://localhost:${port}`);
});
var createError = require('http-errors');
var express = require('express');
var path = require('path');
var cookieParser = require('cookie-parser');
var logger = require('morgan');

var travelRouter = require('./app_server/routes/travel');
//var usersRouter = require('app_server/routes/users');
var indexRouter = require('./app_server/routes/index');
var handlebars = require('hbs');

var app = express();

// view engine setup
app.set('views', path.join(__dirname,'app_server', 'views'));

// register handlebars partials (https://www.npmjs.com/package/hbs)
handlebars.registerPartials(__dirname + '/app_server/views/partials');
app.set('view engine', 'hbs');

app.use(logger('dev'));
app.use(express.json());
app.use(express.urlencoded({ extended: false }));
app.use(cookieParser());
app.use(express.static(path.join(__dirname, 'public')));

app.use('/', indexRouter);
//app.use('/users', usersRouter);
app.use('/travel', travelRouter);

// catch 404 and forward to error handler
app.use(function(req, res, next) {
  next(createError(404));
});

// error handler
app.use(function(err, req, res, next) {
  // set locals, only providing error in development
  res.locals.message = err.message;
  res.locals.error = req.app.get('env') === 'development' ? err : {};
 // res.locals.year = new Date().getFullYear();
  // render the error page
  res.status(err.status || 500);
  res.render('error');
});

// Set port
const PORT = process.env.PORT || 3000;

// Serve static files from public folder
//app.use(express.static(path.join(__dirname, 'public')));

// Start server
app.listen(PORT, () => {
    console.log(`Server running on http://localhost:${PORT}`);
});

module.exports = app;