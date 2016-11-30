# WebService
Restfull WebService Java
package com.ejb3.webservic;

import java.util.HashSet;
import java.util.Set;
import javax.ws.rs.ApplicationPath;
import javax.ws.rs.core.Application;


@ApplicationPath("/restful")
public class MyRestApplication extends Application {
	@Override
	public Set<Class<?>> getClasses()
	{
		Set<Class<?>> classes = new HashSet<Class<?>>();
		classes.add(HelloJAXRSWebService.class);
		return classes;
	}
}
package com.ejb3.webservic;

import javax.ejb.LocalBean;
import javax.ejb.Stateless;
import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.PathParam;
import javax.ws.rs.Produces;

@Stateless
@LocalBean
@Path("/Hesapla")
public class HelloJAXRSWebService {	
	
	@GET
	@Path("/add/{a}/{b}")
	@Produces("text/plain")
	public int add(@PathParam("a") int a , @PathParam("b") int b)
	{
		return (a+b);
	}
		
	@GET
	@Path("/sub/{a}/{b}")
	@Produces("text/plain")
	public int Sub(@PathParam("a") int a , @PathParam("b") int b)
	{
		return (a-b);
	}
	
	@GET
	@Path("/multiply/{a}/{b}")
	@Produces("text/plain")
	public int multiply(@PathParam("a") int a , @PathParam("b") int b)
	{
		return (a*b);
	}
	
	@GET
	@Path("/factorial/{a}")
	@Produces("text/plain")
	public int factorial(@PathParam("a") int a)
	{
		if(a <= 0){
			return 0;
		}
		
		int fact = 1;
		for(int i = 1;i <= a; i++){
			fact = fact*i;
		}
		return fact;
		
						
	}
	
	@GET
	@Path("/mod/{a}/{b}")
	@Produces("text/plain")
	public int Mod(@PathParam("a") int a , @PathParam("b") int b)
	{
		return (a%b);
	}
	
	@GET
	@Path("/devide/{a}/{b}")
	@Produces("text/plain")
	public int division(@PathParam("a") int a , @PathParam("b") int b)
	{
		if(b == 0){
			return -1;
		}

		return a/b;
	}
	
	@GET
	@Path("/fibonacci/{a}")
	@Produces("text/plain")
	public long fibonacci(@PathParam("a") int a )
	{
		if(a <= 0){
			return 0;
		}
		
		long sayi1 = 1,sayi2 = 1,temp = 0;
		
		if(a == 1 || a == 2){
			return 1;
		}
		else		
			for(int i = 0;i < a-2; i++)
			{
				temp = sayi1;
				sayi1 = sayi1 + sayi2;
				sayi2 = temp;
			}
			return sayi1;
	}
}
