require 'sinatra'
require 'pony'
require 'pry'

def send_email(from_user, name, date, description)
  Pony.mail({
    :from => from_user,
    :to => 'lindaseingtran@gmail.com',
    :via => :smtp,
    :subject => "Appointment Request from #{name}",
    :body => "#{name} wants to see you on #{date} for #{description}",
    :via_options => {:address => 'smtp.sendgrid.net',
      :port           => '587',
      :user_name      => 'kineticstudios',
      :password       => 'glossy123',
      :authentication => :plain, # :plain, :login, :cram_md5, no auth by default
      :domain         => "c9.io" # the HELO domain provided by the client to the server
    }

    })
  end





  get "/" do
    erb :"PAGE.html"
  end



  get "/appointments" do
    erb :"appointments.html"
  end
  
  get "/success" do
    erb :"success.html"
end


  post "/email_doctor" do

    send_email(params["from"], params["name"], params["date"], params["description"])
    redirect "/success"
  end
