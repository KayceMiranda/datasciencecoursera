makecachematrix<-function(x=matrix()){
cac<-NULL
set<-function(y) {
x<<-y
cac<<-NULL
}
get<-function()x
setinverse<-function(inverse) cac <<-inverse
getinverse<-function() cac
list (set=set, get=get, setinverse=setinverse, getinverse=getinverse)
}
  
cacheSolve <-function(x, ...){
cac<-x$getinverse()
if(!is.null(cac)){
message( "getting cached data.")
return(cac)
}
data<-x$get()
inv<-solve(data)
x$setinverse(cac)
cac
}  

